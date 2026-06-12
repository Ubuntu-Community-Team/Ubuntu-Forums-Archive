---
title: "JEdit: JCompile (plugin) Error"
date: 2005-12-03
forum: General Help
---

### Post by beelzebub1987 on 2005-12-03
whenever I try to compile anything I get this error:
java.lang.NullPointerException
	at java.util.StringTokenizer.<init>(StringTokenizer.java:182)
	at java.util.StringTokenizer.<init>(StringTokenizer.java:204)
	at javacore.AbstractClasspathSource.loadClassNames(AbstractClasspathSource.java:476)
	at javacore.AbstractClasspathSource.init(AbstractClasspathSource.java:455)
	at javacore.DefaultClasspathSource.<init>(DefaultClasspathSource.java:53)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:39)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:27)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:494)
	at bsh.Reflect.constructObject(Reflect.java:668)
	at bsh.BSHAllocationExpression.constructObject(BSHAllocationExpression.java:123)
	at bsh.BSHAllocationExpression.objectAllocation(BSHAllocationExpression.java:114)
	at bsh.BSHAllocationExpression.eval(BSHAllocationExpression.java:62)
	at bsh.BSHPrimaryExpression.eval(BSHPrimaryExpression.java:102)
	at bsh.BSHPrimaryExpression.eval(BSHPrimaryExpression.java:47)
	at bsh.Interpreter.eval(Interpreter.java:641)
	at bsh.Interpreter.eval(Interpreter.java:731)
	at bsh.Interpreter.eval(Interpreter.java:720)
	at org.gjt.sp.jedit.BeanShell._eval(BeanShell.java:446)
	at org.gjt.sp.jedit.BeanShell.eval(BeanShell.java:410)
	at org.gjt.sp.jedit.ServiceManager$Descriptor.getInstance(ServiceManager.java:321)
	at org.gjt.sp.jedit.ServiceManager.getService(ServiceManager.java:264)
	at javacore.JavaCorePlugin.getClasspathSource(JavaCorePlugin.java:71)
	at javacore.JavaCorePlugin.getClasspathSource(JavaCorePlugin.java:57)
	at jcompiler.JCompiler.getClassPath(JCompiler.java:708)
	at jcompiler.JCompiler.getClassPath(JCompiler.java:728)
	at jcompiler.JCompiler.compile(JCompiler.java:169)
	at jcompiler.JCompilerTask.run(JCompilerTask.java:116)

---

