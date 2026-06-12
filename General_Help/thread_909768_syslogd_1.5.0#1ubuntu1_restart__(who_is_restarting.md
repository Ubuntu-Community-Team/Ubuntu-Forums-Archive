---
title: "syslogd 1.5.0#1ubuntu1: restart  (who is restarting my compy?)"
date: 2008-09-03
forum: General Help
---

### Post by madhusker on 2008-09-03
Just installed 8.04.1 on a Dell 5150 workstation and updated it. I am getting random reboots. And no, it's not hardware because gentoo runs fine on it.  Trying to migrate to ubuntu but this makes it hard. Anyone know how to shut this off?

Sep  3 14:34:36 foo syslogd 1.5.0#1ubuntu1: restart.

# uname -a
Linux foo 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

---

### Post by firfin on 2008-10-23
Hi Husker,
If with random is somewhere from a couple of minutes to hours then I am experiencing the same problem as you with ubuntu 8.04.1 I have completely different hardware setup though. Self-built system based on a Asus P5K motherboard. 
So far I haven't found any useful answers. The hardware runs fine with a dualboot winxp so I don't think that's a problem.
messages and syslog don't show anything for a couple of minutes before the 'ubuntu1: restart' notice

Except for one thing, it has been suggested it might be related to acpi/suspend issues. So when I get home tonight I am gonna try disabling those.  I will let you know how it goes.
( FYI  administration -> services -> power management ( apmd & acpid ) )

---

### Post by djp3 on 2008-10-24
I was having this problem on an HP rack mounted server and it required me to have my systemboard replaced.

No problems since then.

---

### Post by thepocketwade on 2008-12-18
That isn't your computer restarting.  That's syslogd restarting, it will do that after log rotation every morning (or whenever your rotation runs).  There's nothing to worry about, though if you feel the need to stop that log from appearing you can stop log rotation, but that will lead to your log files ballooning in size.

---

### Post by CGH on 2009-05-17
hi, i've been having the same problem, the only thing i could get as an error was:
[code]
org.apache.commons.modeler.Registry registerComponent SEVERE: Error registering Catalina:t
ype=Valve,name=StandardContextValve,path=/jsp-examples,host=localhost javax.management.MBeanException: Cannot instantiate ModelMBean of class org.apache.comm
ons.modeler.BaseModelMBean ^Iat org.apache.commons.modeler.ManagedBean.createMBean(ManagedBean.java:385) ^Iat org.apache.commons.modeler.Registry.registerCom
ponent(Registry.java:835) ^Iat org.apache.catalina.core.StandardPipeline.registerValve(StandardPipeline.java:302) ^Iat org.apache.catalina.core.StandardPipel
ine.start(StandardPipeline.java:234) ^Iat org.apache.catalina.core.StandardContext.start(StandardContext.java:4140) ^Iat org.apache.catalina.core.ContainerBa
se.addChildInternal(ContainerBase.java:760) ^Iat org.apache.catalina.core.ContainerBase.access$0(ContainerBase.java:744) ^Iat org.apache.catalina.core.Contai
nerBase$PrivilegedAddChild.run(ContainerBase.java:144) ^Iat java.security.AccessController.d
May 15 12:54:32 dell-desktop jsvc.exec[5923]: talina.core.ContainerBase.addChild(ContainerBase.java:738) ^Iat org.apache.catalina.core.StandardHost.addChild(
StandardHost.java:544) ^Iat org.apache.catalina.startup.HostConfig.deployDescriptor(HostConfig.java:626) ^Iat org.apache.catalina.startup.HostConfig.deployDe
scriptors(HostConfig.java:553) ^Iat org.apache.catalina.startup.HostConfig.deployApps(HostConfig.java:488) ^Iat org.apache.catalina.startup.HostConfig.start(
HostConfig.java:1138) ^Iat org.apache.catalina.startup.HostConfig.lifecycleEvent(HostConfig.java:311) ^Iat org.apache.catalina.util.LifecycleSupport.fireLife
cycleEvent(LifecycleSupport.java:120) ^Iat org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1022) ^Iat org.apache.catalina.core.StandardHost.s
tart(StandardHost.java:736) ^Iat org.apache.catalina.core.ContainerBase.start(ContainerBase.java:1014) ^Iat org.apache.catalina.core.StandardEngine.start(Sta
ndardEngine.java:443) ^Iat org.apache.catalina.core.StandardService.start(StandardService.ja
May 15 12:54:32 dell-desktop jsvc.exec[5923]: rver.start(StandardServer.java:700) ^Iat org.apache.catalina.startup.Catalina.start(Catalina.java:552) ^Iat sun
.reflect.NativeMethodAccessorImpl.invoke0(Native Method) ^Iat sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39) ^Iat sun.reflect.
DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25) ^Iat java.lang.reflect.Method.invoke(Method.java:597) ^Iat org.apache.catalina.star
tup.Bootstrap.start(Bootstrap.java:295) ^Iat sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method) ^Iat sun.reflect.NativeMethodAccessorImpl.invoke(Nat
iveMethodAccessorImpl.java:39) ^Iat sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25) ^Iat java.lang.reflect.Method.invok
e(Method.java:597) ^Iat org.apache.commons.daemon.support.DaemonLoader.start(DaemonLoader.java:177) Caused by: java.security.AccessControlException: access d
enied (java.io.FilePermission /usr/share/tomcat5.5-webapps/jsp-examples/WEB-INF/classes/logg
[\code]

but i don't use tomcat, maybe that's the error

Saludos!

---

### Post by paulororke on 2009-12-09
I'm seeing the same thing.  If that line about syslog is not about the system restart it must be the first thisng recorded in /var/log/messages after the restart

Dec  8 21:01:32 wss-vmserv-01 -- MARK --
Dec  8 21:21:32 wss-vmserv-01 -- MARK --
Dec  8 21:41:32 wss-vmserv-01 -- MARK --
Dec  8 22:01:32 wss-vmserv-01 -- MARK --
Dec  8 23:11:58 wss-vmserv-01 syslogd 1.5.0#1ubuntu1: restart.
Dec  8 23:11:58 wss-vmserv-01 kernel: Inspecting /boot/System.map-2.6.24-19-server
Dec  8 23:11:58 wss-vmserv-01 kernel: Loaded 28734 symbols from /boot/System.map-2.6.24-19-server.
Dec  8 23:11:58 wss-vmserv-01 kernel: Symbols match kernel version 2.6.24.
Dec  8 23:11:58 wss-vmserv-01 kernel: Loaded 14437 symbols from 58 modules.
Dec  8 23:11:58 wss-vmserv-01 kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec  8 23:11:58 wss-vmserv-01 kernel: [    0.000000] Initializing cgroup subsys cpu
Dec  8 23:11:58 wss-vmserv-01 kernel: [    0.000000] Linux version 2.6.24-19-server (buildd@yellow) (gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)) #1 SMP Wed Jun 18 14:44:47 UTC 2008 (Ubuntu 2.6.24-19.34-server).......

This machine is an Ubuntu 8.04 home built.

---

