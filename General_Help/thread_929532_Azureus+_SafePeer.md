---
title: "Azureus+ SafePeer"
date: 2008-09-25
forum: General Help
---

### Post by FLCL on 2008-09-25
I installed the safepeer plugin for azureus, current stable build being 2.5.2 and it fails to initialize. I've tried the only fix that others claim to have worked for them, but not no avail. This is what it tells me in details:

> java.lang.NoClassDefFoundError: org/apache/commons/httpclient/HttpMethod
	at org.ludo.safepeer.SafePeer.<init>(SafePeer.java:72)
	at org.ludo.plugins.azureus.AzureusIpFilterExporter.export(AzureusIpFilterExporter.java:233)
	at org.ludo.plugins.azureus.AzureusIpFilterExporter.initialize(AzureusIpFilterExporter.java:168 )
	at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.initialisePlugin(PluginInitializer.java:1093)
	at org.gudy.azureus2.pluginsimpl.local.PluginInitializer.initialisePlugins(PluginInitializer.java:968 )
	at com.aelitis.azureus.core.impl.AzureusCoreImpl.start(AzureusCoreImpl.java:428 )
	at org.gudy.azureus2.ui.swt.mainwindow.Initializer.run(Initializer.java:301)
	at org.gudy.azureus2.ui.swt.mainwindow.SWTThread$1.runSupport(SWTThread.java:124)
	at org.gudy.azureus2.core3.util.AERunnable.run(AERunnable.java:38 )
	at java.lang.Thread.run(Thread.java:636)
Caused by: java.lang.ClassNotFoundException: org.apache.commons.httpclient.HttpMethod
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268 )
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:336)
	... 10 more

So i followed this "fix" which states:
> Had exactly the same problem.  Got it to work by putting the missing files
in the azureus directory:

commons-codec-1.3.jar
commons-logging-1.1.1.jar
commons-httpclient-3.1.jar

all can be downloaded from [http://commons.apache.org/](http://commons.apache.org/)
also changed the URL for the list to:
[http://www.bluetack.co.uk/config/level1.zip](http://www.bluetack.co.uk/config/level1.zip)
I disabled "enable blocklist manager" in the safepeer preferences.

this worked for me.

Pd.

I've tried and it still gives me the error :(. Another thing is it generally stated the azureus directory, so I'm asusming that means the main  "home" folder for azureus so to speak. Although there are 2, .Azureus and .azureus. The latter contains configuration files and what not, while the first just a single plugin folder with updater in it. So i put them in .azureus.

Can anyone help me out please? :(

---

### Post by FLCL on 2008-09-25
Bump

---

### Post by ethos101 on 2008-09-30
Bump, same problem.

---

### Post by Mikael.Ernholm on 2008-11-12
The problem is that the files must also be added to the java classpath.

The easiest way to work around this problem is to remove Azureus in Synaptic and download it from [www.azereus.org](www.azereus.org) and put the files from Apache mentioned above in the same directory.

If you don't want to do that, you will have to manually edit the /usr/bin/azureus file and add the jar-files. If you have put them in the ~/.azureus directory it will look something like this:

```
#!/bin/sh
JAVA='java -Xmx1024M'
if [ -x /usr/bin/vuze ]; then
	FORCEUI='';
else
	FORCEUI='-Dforce.ui=az2';
fi

. /usr/share/java-config/libswt-3.4-java

# Add jar files to the classpath
for FILE in ~/.azureus/*.jar; do
	JARS="${JARS:+${JARS}:}$FILE"
done

exec $JAVA -Djava.library.path=/usr/lib/jni:/usr/lib \
	-classpath /usr/share/java/Azureus2.jar:$JARS \
	-Dazureus.install.path="$HOME/.azureus" \
	-Dazureus.config.path="$HOME/.azureus" \
	$FORCEUI \
	org.gudy.azureus2.ui.common.Main "$@"
```

Good luck!

---

### Post by Steve1961 on 2008-11-12
It's also worth giving Deluge a try as that has the safepeer plugin functionality as well.

---

### Post by haylun98 on 2008-11-12
Is Safepeer better than ipfilter?

I use ipfilter and manually download the block list from Bluetack

---

### Post by Steve1961 on 2008-11-12
> **haylun98 said:**
> Is Safepeer better than ipfilter?

I use ipfilter and manually download the block list from Bluetack

As both use bluetack blocklists I'm not sure there's that much difference.  It's also questionable just how much protection they provide, although something is obviously better than nothing :)

---

