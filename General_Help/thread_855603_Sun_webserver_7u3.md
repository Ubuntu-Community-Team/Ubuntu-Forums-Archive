---
title: "Sun webserver 7u3"
date: 2008-07-10
forum: General Help
---

### Post by gert cuykens on 2008-07-10
I have problems installing sun webserver 7 on ubuntu 8

```

Jul 10, 2008 8:51:18 PM com.sun.web.installer.common.dialogs.CustomDirectorySelectionPanel isDisplayComplete
INFO: Installing Sun Java System Web Server 7.0U3 (64-Bit)
Jul 10, 2008 8:54:44 PM com.sun.web.installer.web.actions.PostInstall_core install
INFO: Start core server configuration
Jul 10, 2008 8:54:44 PM com.sun.web.installer.web.actions.PostInstall_core configureServer
INFO: Invoking the server configuration script
Jul 10, 2008 9:54:45 PM com.sun.web.admin.configurator.ConfigureServer main
INFO: ADMIN2000: Configuring Sun Java System Web Server 7.0U3 (64-Bit) B06/16/2008 11:05 on Linux 2.6.24.5-grsec-xxxx-grs-ipv4-64 amd64
Jul 10, 2008 9:54:46 PM com.sun.web.admin.configurator.ConfigureServer main
FINE: Input tokens: {WS_ADMIN_IS_SERVER_MODE=true, WS_ADMIN_SSL_PORT=8989, WS_NODE_SSL_PORT=8989, WS_CONFIG_NAME=ns22130.ovh.net, WS_NODE_HOST=ns22130.ovh.net
Jul 10, 2008 9:54:46 PM com.sun.web.admin.configurator.ConfigureServer <init>
FINEST: In ConfigureServer constructor
Jul 10, 2008 9:54:46 PM com.sun.web.admin.configurator.ConfigureServer configureServer
FINEST: In ConfigureServer.configureServer()
Jul 10, 2008 9:54:46 PM com.sun.web.admin.configurator.ConfigureServer configureServer
FINEST: Checking availability of common tokens...
Jul 10, 2008 9:54:46 PM com.sun.web.admin.configurator.ConfigureServer main
WARNING: /sun/webserver7/lib/libadminjni.so: libstdc++.so.5: cannot open shared object file: No such file or directory
java.lang.UnsatisfiedLinkError: /sun/webserver7/lib/libadminjni.so: libstdc++.so.5: cannot open shared object file: No such file or directory
    at java.lang.ClassLoader$NativeLibrary.load(Native Method)
    at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1676)
    at java.lang.Runtime.loadLibrary0(Runtime.java:823)
    at java.lang.System.loadLibrary(System.java:1030)
    at com.sun.web.admin.util.Util.loadAdminJNILibrary(Util.java:147)
    at com.sun.web.admin.util.ProcessRunner.<clinit>(ProcessRunner.java:189)
    at com.sun.web.admin.util.PlatformUtil.validateJavaHome(PlatformUtil.java:54)
    at com.sun.web.admin.configurator.ConfigureServer.configureServer(ConfigureServer.java:525)
    at com.sun.web.admin.configurator.ConfigureServer.main(ConfigureServer.java:68)
Jul 10, 2008 9:54:46 PM com.sun.web.admin.configurator.ConfigureServer printFailedMessage
FINE: ADMIN2001: Error occurred during configuration of server instances
Jul 10, 2008 8:54:46 PM com.sun.web.installer.web.actions.PostInstall_core configureServer
WARNING: The backend configurator failed
                                          

```

---

### Post by Vadi on 2008-07-10
What package was it or how did you get it?

---

### Post by gert cuykens on 2008-07-10
donwloaded the 64bit jdk6u7 from sun and the 64bit webserver7u3 from sun

---

### Post by Vadi on 2008-07-10
Have you tried contacting their support on it?

---

### Post by gert cuykens on 2008-07-10
no because they are going to say its ubuntu :-)

---

### Post by Vadi on 2008-07-10
Well, this is the sun installer failing here. If they say it's ubuntu, they'll at least say what the issue is.

---

### Post by gert cuykens on 2008-07-10
(The sun forum seems to be having some troubles it self, i can not login. )

Do you also have the same setup failure on your ubuntu ?

---

### Post by Vadi on 2008-07-10
Don't know, but getting java browser plugin to work on 64bit was a pain and I don't feel like experimenting with it again. Sorry.

---

### Post by meenav on 2009-09-07
Please try 
$sudo apt-get install libstdc++5

 If you get an error /bin/domainname not found, you need to 

$sudo apt-get install nis

I have tested on Ubuntu 9.04. 

For any such questions about Sun's Web Server please use Web Server's forum [http://forums.sun.com/forum.jspa?forumID=759](http://forums.sun.com/forum.jspa?forumID=759) 

Refer these blogs about How to install Sun's Web Server on CentOS, Fedora and Ubuntu 
[http://blogs.sun.com/meena/entry/installing_sun_web_server_on ]("http://blogs.sun.com/meena/entry/installing_sun_web_server_on")
[http://jmccabe.org/blog/CentOS_WebServer_Install](http://jmccabe.org/blog/CentOS_WebServer_Install)
[http://blogs.sun.com/kkranz/entry/installing_sun_java_system_web](http://blogs.sun.com/kkranz/entry/installing_sun_java_system_web)
[http://wikis.sun.com/display/WebServer/Installing+on+Ubuntu](http://wikis.sun.com/display/WebServer/Installing+on+Ubuntu)

---

### Post by korb on 2009-11-08
Meena,

I have posted on your blog, too. I cannot get this working on Ubuntu 9.10, Karmic Koala. Have you tried yet? It looks like they have moved to libstdc++6, and libstdc++5 is not available.

Thanks,
Bill

---

### Post by meenav on 2009-11-09
Please report all Sun Web Server related problems in [http://forums.sun.com/forum.jspa?forumID=759](http://forums.sun.com/forum.jspa?forumID=759)

Lets discuss this issue in [http://forums.sun.com/thread.jspa?threadID=5415159&tstart=0](http://forums.sun.com/thread.jspa?threadID=5415159&tstart=0)

---

