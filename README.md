# Springboot-customRestTemplateBuilder-interceptor

* Using Interceptor we have one place of logging for every request because the request goes through the interceptor before executing the MainController method.
* RestTemplateBuilder is used to customize the resttemplate
* Using restTemplateBuilder we can fetch the data in `userManagementApp` using"
    > http://localhost:8080/userList
  
### The flow of restTemplate using custom restTemplateBuilder in this application is:
* First the request hit the `getUserList` method of `MainController` class  which required restTemplate.
* RestTemplate is autowired so it will go to `Config` class and find the `restTemplate` bean.
* RestTemplate bean in Config class is has RestTemplateBuilder as parameter.
* In the config there is the bean for `RestTemplateBuilder` which depends on `RestTemplateCustomizer`. If there is no `RestTemplateCustomizer` it will throw error.
* restTemplateCustomizer return the instance of `MyRestTemplateCustomizer`.
* `MyRestTemplateCustomizer` inject  `MyRequestInterceptor`
* `MyRequestInterceptor` required `MyClientHttpResponse` to show the actual response. 