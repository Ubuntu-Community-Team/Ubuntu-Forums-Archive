---
title: "[Eclipse + Apache Geronimo v.2.1]"
date: 2008-10-27
forum: General Help
---

### Post by [Tenshi] on 2008-10-27
Hiya everybody, I got a little problem, I add  my dynamic web project to the server (Apache Geronimo 2.1) then I tried to deploy the application but I have this message, does anyone help me?

```

Distribution of module failed.  See log for details.
  Cannot deploy the requested application module because no deployer is able to handle it.  This can happen if you have omitted the J2EE deployment descriptor, disabled a deployer module, or if, for example, you are trying to deploy an EJB module on a minimal Geronimo server that does not have EJB support installed.  (moduleFile=/tmp/geronimo-deployer34243.tmpdir/ContentManagerEAR.zip)
  org.apache.geronimo.common.DeploymentException: Cannot deploy the requested application module because no deployer is able to handle it.  This can happen if you have omitted the J2EE deployment descriptor, disabled a deployer module, or if, for example, you are trying to deploy an EJB module on a minimal Geronimo server that does not have EJB support installed.  (moduleFile=/tmp/geronimo-deployer34243.tmpdir/ContentManagerEAR.zip)
  	at org.apache.geronimo.deployment.Deployer.deploy(Deployer.java:233)
  	at org.apache.geronimo.deployment.Deployer.deploy(Deployer.java:133)
  	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
  	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
  	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
  	at java.lang.reflect.Method.invoke(Method.java:597)
  	at org.apache.geronimo.gbean.runtime.ReflectionMethodInvoker.invoke(ReflectionMethodInvoker.java:34)
  	at org.apache.geronimo.gbean.runtime.GBeanOperation.invoke(GBeanOperation.java:124)
  	at org.apache.geronimo.gbean.runtime.GBeanInstance.invoke(GBeanInstance.java:867)
  	at org.apache.geronimo.kernel.basic.BasicKernel.invoke(BasicKernel.java:239)
  	at org.apache.geronimo.kernel.KernelGBean.invoke(KernelGBean.java:342)
  	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
  	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
  	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
  	at java.lang.reflect.Method.invoke(Method.java:597)
  	at org.apache.geronimo.gbean.runtime.ReflectionMethodInvoker.invoke(ReflectionMethodInvoker.java:34)
  	at org.apache.geronimo.gbean.runtime.GBeanOperation.invoke(GBeanOperation.java:124)
  	at org.apache.geronimo.gbean.runtime.GBeanInstance.invoke(GBeanInstance.java:867)
  	at org.apache.geronimo.kernel.basic.BasicKernel.invoke(BasicKernel.java:239)
  	at org.apache.geronimo.system.jmx.MBeanGBeanBridge.invoke(MBeanGBeanBridge.java:172)
  	at com.sun.jmx.interceptor.DefaultMBeanServerInterceptor.invoke(DefaultMBeanServerInterceptor.java:836)
  	at com.sun.jmx.mbeanserver.JmxMBeanServer.invoke(JmxMBeanServer.java:761)
  	at javax.management.remote.rmi.RMIConnectionImpl.doOperation(RMIConnectionImpl.java:1426)
  	at javax.management.remote.rmi.RMIConnectionImpl.access$200(RMIConnectionImpl.java:72)
  	at javax.management.remote.rmi.RMIConnectionImpl$PrivilegedOperation.run(RMIConnectionImpl.java:1264)
  	at java.security.AccessController.doPrivileged(Native Method)
  	at javax.management.remote.rmi.RMIConnectionImpl.doPrivilegedOperation(RMIConnectionImpl.java:1366)
  	at javax.management.remote.rmi.RMIConnectionImpl.invoke(RMIConnectionImpl.java:788)
  	at sun.reflect.GeneratedMethodAccessor52.invoke(Unknown Source)
  	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
  	at java.lang.reflect.Method.invoke(Method.java:597)
  	at sun.rmi.server.UnicastServerRef.dispatch(UnicastServerRef.java:305)
  	at sun.rmi.transport.Transport$1.run(Transport.java:159)
  	at java.security.AccessController.doPrivileged(Native Method)
  	at sun.rmi.transport.Transport.serviceCall(Transport.java:155)
  	at sun.rmi.transport.tcp.TCPTransport.handleMessages(TCPTransport.java:535)
  	at sun.rmi.transport.tcp.TCPTransport$ConnectionHandler.run0(TCPTransport.java:790)
  	at sun.rmi.transport.tcp.TCPTransport$ConnectionHandler.run(TCPTransport.java:649)
  	at java.util.concurrent.ThreadPoolExecutor$Worker.runTask(ThreadPoolExecutor.java:885)
  	at java.util.concurrent.ThreadPoolExecutor$Worker.run(ThreadPoolExecutor.java:907)
  	at java.lang.Thread.run(Thread.java:619)

```

---

