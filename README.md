# my-sts-spring-basic
나의 스프링 기초   
먼저 STS 로 스프링의 기초를 잡는다.   

## .gitignore
아래의 주소에서 Maven,Java,Windows,Eclipse 항목을 추가후 생성
https://www.toptal.com/developers/gitignore   

생성된 내용을 .gitignore 파일에 추가

## Workspace 기본설정 구성
처음 프로젝트 생성후   
##### Window/Preferences/Spring/Template Projects

spring-defaults 항목만 남기고 모두 제거 후   

##### Apply and Close   
</br>

+ 파일 인코딩 UTF-8 설정
Window/Preferences/type filter text -> encoding   
General/Workspace   
Web/CSS Files, HTML Files, JSP Files   
XML/XML Files




## 프로젝트 구성
+ 인코딩 필터 설정
src/main/webapp/WEB-INF/web.xml
```
<servlet-mapping>
	<servlet-name>appServlet</servlet-name>
	<url-pattern>/</url-pattern>
</servlet-mapping>

<!-- 인코딩 필터 설정 -->
<filter>
	<filter-name>encodingFilter</filter-name>
	<filter-class>org.springframework.web.filter.CharacterEncodingFilter</filter-class>
	<init-param>
		<param-name>encoding</param-name>
		<param-value>UTF-8</param-value>
	</init-param>
	<init-param>
		<!-- 요청,응답 모두 인코딩 처리 -->
		<param-name>forceEncoding</param-name>
		<param-value>true</param-value>
	</init-param>
</filter>
```

</br>

### Basic1

##### 1. @Controller   
```
@Controller
public class RequestMappingController {

}
```

##### 2. @RequestMapping 

RequestMappingController.java
```
@RequestMapping(value = {}, method = { RequestMethod.GET})
public void request(HttpServletRequest request, HttpServletResponse response) {

}
```
value = 매핑주소   
method = 요청 방법

SPRING에서는 내부적으로 매핑주소(value)를 request 메서드로 매핑   
##### org.springframework.web.servlet.mvc.method.annotation.RequestMappingHandlerMapping   



RequestMapping 어노테이션 기능이 개선된 애너테이션은 아래와 같습니다.

+ @DeleteMapping
+ @GetMapping
+ @PatchMapping
+ @PostMapping
+ @PutMapping

SPRING 4.3 버전부터 사용이 가능하며 아래와 같이 사용할 수 있습니다.
```
@Controller
@RequestMapping("/request)
public class RequestMappingController {

	@GetMapping("/process1")
	public void process1() {

	}
}
```
process1 메서드에서는 /request/process1 의 Url 과 매핑됩니다.

</br>
</br>
</br>
추후에 Intelij 로 해당 프로젝트 그대로 이관작업 예정
