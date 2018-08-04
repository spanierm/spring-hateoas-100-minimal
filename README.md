# Spring HATEOAS 1.0.0.BUILD-SNAPSHOT Build Issue Example

Minimal example using Spring HATEOAS's `1.0.0.BUILD-SNAPSHOT` version.
When running the tests with `mvn clean verify`,
  loading the context in the test in [`SpringHateoas100MinimalApplicationTests`](src/test/java/com/example/springhateoas100minimal/SpringHateoas100MinimalApplicationTests.java)
  fails with a `NoUniqueBeanDefinitionException` exception:
```text
***************************
APPLICATION FAILED TO START
***************************

Description:

Parameter 0 of method linkDiscoverers in org.springframework.hateoas.config.HateoasConfiguration required a single bean, but 3 were found:
	- entityLinksPluginRegistry: defined by method 'entityLinksPluginRegistry' in class path resource [org/springframework/hateoas/config/EntityLinksConfiguration.class]
	- relProviderPluginRegistry: defined by method 'relProviderPluginRegistry' in class path resource [org/springframework/hateoas/config/HateoasConfiguration.class]
	- linkDiscovererRegistry: defined in null


Action:

Consider marking one of the beans as @Primary, updating the consumer to accept multiple beans, or using @Qualifier to identify the bean that should be consumed

2018-08-04 12:41:11.123 ERROR 23639 --- [           main] o.s.test.context.TestContextManager      : Caught exception while allowing TestExecutionListener [org.springframework.test.context.web.ServletTestExecutionListener@f6efaab] to prepare test instance [com.example.springhateoas100minimal.SpringHateoas100MinimalApplicationTests@4d6f197e]

java.lang.IllegalStateException: Failed to load ApplicationContext
	at org.springframework.test.context.cache.DefaultCacheAwareContextLoaderDelegate.loadContext(DefaultCacheAwareContextLoaderDelegate.java:125) ~[spring-test-5.0.8.RELEASE.jar:5.0.8.RELEASE]
	at org.springframework.test.context.support.DefaultTestContext.getApplicationContext(DefaultTestContext.java:108) ~[spring-test-5.0.8.RELEASE.jar:5.0.8.RELEASE]
	at org.springframework.test.context.web.ServletTestExecutionListener.setUpRequestContextIfNecessary(ServletTestExecutionListener.java:190) ~[spring-test-5.0.8.RELEASE.jar:5.0.8.RELEASE]
	at org.springframework.test.context.web.ServletTestExecutionListener.prepareTestInstance(ServletTestExecutionListener.java:132) ~[spring-test-5.0.8.RELEASE.jar:5.0.8.RELEASE]
	at org.springframework.test.context.TestContextManager.prepareTestInstance(TestContextManager.java:246) ~[spring-test-5.0.8.RELEASE.jar:5.0.8.RELEASE]
	at org.springframework.test.context.junit4.SpringJUnit4ClassRunner.createTest(SpringJUnit4ClassRunner.java:227) [spring-test-5.0.8.RELEASE.jar:5.0.8.RELEASE]
	at org.springframework.test.context.junit4.SpringJUnit4ClassRunner$1.runReflectiveCall(SpringJUnit4ClassRunner.java:289) [spring-test-5.0.8.RELEASE.jar:5.0.8.RELEASE]
	at org.junit.internal.runners.model.ReflectiveCallable.run(ReflectiveCallable.java:12) [junit-4.12.jar:4.12]
	at org.springframework.test.context.junit4.SpringJUnit4ClassRunner.methodBlock(SpringJUnit4ClassRunner.java:291) [spring-test-5.0.8.RELEASE.jar:5.0.8.RELEASE]
	at org.springframework.test.context.junit4.SpringJUnit4ClassRunner.runChild(SpringJUnit4ClassRunner.java:246) [spring-test-5.0.8.RELEASE.jar:5.0.8.RELEASE]
	at org.springframework.test.context.junit4.SpringJUnit4ClassRunner.runChild(SpringJUnit4ClassRunner.java:97) [spring-test-5.0.8.RELEASE.jar:5.0.8.RELEASE]
	at org.junit.runners.ParentRunner$3.run(ParentRunner.java:290) [junit-4.12.jar:4.12]
	at org.junit.runners.ParentRunner$1.schedule(ParentRunner.java:71) [junit-4.12.jar:4.12]
	at org.junit.runners.ParentRunner.runChildren(ParentRunner.java:288) [junit-4.12.jar:4.12]
	at org.junit.runners.ParentRunner.access$000(ParentRunner.java:58) [junit-4.12.jar:4.12]
	at org.junit.runners.ParentRunner$2.evaluate(ParentRunner.java:268) [junit-4.12.jar:4.12]
	at org.springframework.test.context.junit4.statements.RunBeforeTestClassCallbacks.evaluate(RunBeforeTestClassCallbacks.java:61) [spring-test-5.0.8.RELEASE.jar:5.0.8.RELEASE]
	at org.springframework.test.context.junit4.statements.RunAfterTestClassCallbacks.evaluate(RunAfterTestClassCallbacks.java:70) [spring-test-5.0.8.RELEASE.jar:5.0.8.RELEASE]
	at org.junit.runners.ParentRunner.run(ParentRunner.java:363) [junit-4.12.jar:4.12]
	at org.springframework.test.context.junit4.SpringJUnit4ClassRunner.run(SpringJUnit4ClassRunner.java:190) [spring-test-5.0.8.RELEASE.jar:5.0.8.RELEASE]
	at org.apache.maven.surefire.junit4.JUnit4Provider.execute(JUnit4Provider.java:365) [surefire-junit4-2.21.0.jar:2.21.0]
	at org.apache.maven.surefire.junit4.JUnit4Provider.executeWithRerun(JUnit4Provider.java:273) [surefire-junit4-2.21.0.jar:2.21.0]
	at org.apache.maven.surefire.junit4.JUnit4Provider.executeTestSet(JUnit4Provider.java:238) [surefire-junit4-2.21.0.jar:2.21.0]
	at org.apache.maven.surefire.junit4.JUnit4Provider.invoke(JUnit4Provider.java:159) [surefire-junit4-2.21.0.jar:2.21.0]
	at org.apache.maven.surefire.booter.ForkedBooter.invokeProviderInSameClassLoader(ForkedBooter.java:379) [surefire-booter-2.21.0.jar:2.21.0]
	at org.apache.maven.surefire.booter.ForkedBooter.runSuitesInProcess(ForkedBooter.java:340) [surefire-booter-2.21.0.jar:2.21.0]
	at org.apache.maven.surefire.booter.ForkedBooter.execute(ForkedBooter.java:125) [surefire-booter-2.21.0.jar:2.21.0]
	at org.apache.maven.surefire.booter.ForkedBooter.main(ForkedBooter.java:413) [surefire-booter-2.21.0.jar:2.21.0]
Caused by: org.springframework.beans.factory.UnsatisfiedDependencyException: Error creating bean with name 'linkDiscoverers' defined in class path resource [org/springframework/hateoas/config/HateoasConfiguration.class]: Unsatisfied dependency expressed through method 'linkDiscoverers' parameter 0; nested exception is org.springframework.beans.factory.NoUniqueBeanDefinitionException: No qualifying bean of type 'org.springframework.plugin.core.PluginRegistry<?, ?>' available: expected single matching bean but found 3: entityLinksPluginRegistry,relProviderPluginRegistry,linkDiscovererRegistry
	at org.springframework.beans.factory.support.ConstructorResolver.createArgumentArray(ConstructorResolver.java:732) ~[spring-beans-5.0.8.RELEASE.jar:5.0.8.RELEASE]
	at org.springframework.beans.factory.support.ConstructorResolver.instantiateUsingFactoryMethod(ConstructorResolver.java:474) ~[spring-beans-5.0.8.RELEASE.jar:5.0.8.RELEASE]
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.instantiateUsingFactoryMethod(AbstractAutowireCapableBeanFactory.java:1247) ~[spring-beans-5.0.8.RELEASE.jar:5.0.8.RELEASE]
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBeanInstance(AbstractAutowireCapableBeanFactory.java:1096) ~[spring-beans-5.0.8.RELEASE.jar:5.0.8.RELEASE]
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:535) ~[spring-beans-5.0.8.RELEASE.jar:5.0.8.RELEASE]
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:495) ~[spring-beans-5.0.8.RELEASE.jar:5.0.8.RELEASE]
	at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:317) ~[spring-beans-5.0.8.RELEASE.jar:5.0.8.RELEASE]
	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:222) ~[spring-beans-5.0.8.RELEASE.jar:5.0.8.RELEASE]
	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:315) ~[spring-beans-5.0.8.RELEASE.jar:5.0.8.RELEASE]
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:199) ~[spring-beans-5.0.8.RELEASE.jar:5.0.8.RELEASE]
	at org.springframework.beans.factory.support.DefaultListableBeanFactory.preInstantiateSingletons(DefaultListableBeanFactory.java:759) ~[spring-beans-5.0.8.RELEASE.jar:5.0.8.RELEASE]
	at org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:869) ~[spring-context-5.0.8.RELEASE.jar:5.0.8.RELEASE]
	at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:550) ~[spring-context-5.0.8.RELEASE.jar:5.0.8.RELEASE]
	at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:762) ~[spring-boot-2.0.4.RELEASE.jar:2.0.4.RELEASE]
	at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:398) ~[spring-boot-2.0.4.RELEASE.jar:2.0.4.RELEASE]
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:330) ~[spring-boot-2.0.4.RELEASE.jar:2.0.4.RELEASE]
	at org.springframework.boot.test.context.SpringBootContextLoader.loadContext(SpringBootContextLoader.java:139) ~[spring-boot-test-2.0.4.RELEASE.jar:2.0.4.RELEASE]
	at org.springframework.test.context.cache.DefaultCacheAwareContextLoaderDelegate.loadContextInternal(DefaultCacheAwareContextLoaderDelegate.java:99) ~[spring-test-5.0.8.RELEASE.jar:5.0.8.RELEASE]
	at org.springframework.test.context.cache.DefaultCacheAwareContextLoaderDelegate.loadContext(DefaultCacheAwareContextLoaderDelegate.java:117) ~[spring-test-5.0.8.RELEASE.jar:5.0.8.RELEASE]
	... 27 common frames omitted
Caused by: org.springframework.beans.factory.NoUniqueBeanDefinitionException: No qualifying bean of type 'org.springframework.plugin.core.PluginRegistry<?, ?>' available: expected single matching bean but found 3: entityLinksPluginRegistry,relProviderPluginRegistry,linkDiscovererRegistry
	at org.springframework.beans.factory.config.DependencyDescriptor.resolveNotUnique(DependencyDescriptor.java:215) ~[spring-beans-5.0.8.RELEASE.jar:5.0.8.RELEASE]
	at org.springframework.beans.factory.support.DefaultListableBeanFactory.doResolveDependency(DefaultListableBeanFactory.java:1113) ~[spring-beans-5.0.8.RELEASE.jar:5.0.8.RELEASE]
	at org.springframework.beans.factory.support.DefaultListableBeanFactory.resolveDependency(DefaultListableBeanFactory.java:1062) ~[spring-beans-5.0.8.RELEASE.jar:5.0.8.RELEASE]
	at org.springframework.beans.factory.support.ConstructorResolver.resolveAutowiredArgument(ConstructorResolver.java:818) ~[spring-beans-5.0.8.RELEASE.jar:5.0.8.RELEASE]
	at org.springframework.beans.factory.support.ConstructorResolver.createArgumentArray(ConstructorResolver.java:724) ~[spring-beans-5.0.8.RELEASE.jar:5.0.8.RELEASE]
	... 45 common frames omitted
```
