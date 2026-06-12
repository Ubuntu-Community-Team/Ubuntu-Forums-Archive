---
title: "Firefox 3 - Java plugin problem"
date: 2008-07-14
forum: General Help
---

### Post by Kleenux on 2008-07-14
I keep having the "Java plugin missing" in Firefox 3. (On Linux Ubuntu 7.10)

Downloaded the latest JRE jre1.6.0_10 with the brand new plugin libjavaplugin_oji.so.
Copied libjavaplugin_oji.so to the new FF dir in plugins.

However, after restart, neither "about: plugins", nor Tools/Add-ons/Plugins show the java plugin.

[ To ensure this is the right dir, I removed the flash plugin from there and it disappears from the plugins - so this is the right dir!]

Tried many (many) things, like updating /etc/alternatives, update the older FF versions plugins ....
Java plugin doesn't show :confused:

Please help.

---

### Post by ajgreeny on 2008-07-14
Have you tried ```
sudo update-alternatives --config java
``` in terminal.  That may do no more than you say you have already done updating /etc/alternatives but I don't actually know what the command changes.

---

### Post by Kleenux on 2008-07-14
Hi ajgreeny, thank you for your post and the command.

- I uninstalled java and alternatives (using the command)
- reinstalled java from synaptic
=> only 1 alternative (that doesn't work in FF3...)
- added my new alternative (new jre with special plugin for FF3)
=> no luck either

This is the result of your command

```
root@myserver:~# update-alternatives --config mozilla-javaplugin.so

There are 2 alternatives which provide `mozilla-javaplugin.so'.

Selection Alternative
----------------------------------------
   1    /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
*+ 2    /root/jre1.6.0_10/plugin/i386/ns7/libjavaplugin_oji.so
```
And this is my plugins list in FF3
```
root@mysevrer:~# ls -l /usr/local/firefox/plugins
total 8188
-rwxr-xr-x 1 root root 8115888 2008-06-18 10:29 libflashplayer.so
-rwxr-xr-x 1 root root  137021 2008-07-14 13:05 libjavaplugin_oji.so
-rwxr-xr-x 1 root root   15792 2008-05-30 05:21 libnullplugin.so
-rw-r--r-- 1 root root   99460 2008-03-12 07:26 libvlcplugin.so
drwxr-xr-x 2 root root     320 2008-07-14 13:08 nono
lrwxrwxrwx 1 root root      39 2008-07-10 19:33 nphelix.so -> /opt/real/RealPlayer/mozilla/nphelix.so

```

Tools/Add-ons/Plugins still doesn't show Java (neither about: plugins) :-(

---

### Post by raptor2552 on 2008-07-14
I think that plugin or a link to the plugin belongs in /usr/lib/firefox-addons/plugins. This way when or if you ever upgrade FF it will always find the plugin.

As an example I put the Java release in: /usr/lib/java/jre1.6.0_06 so the shared lib is in: /usr/lib/java/jre1.6.0_06/plugin/i386/ns7/libjavaplugin_oji.so

then in /usr/lib/firefox-addons/plugins added a link to the shared library
```
ln -s /usr/lib/java/jre1.6.0_06/plugin/i386/ns7/libjavaplugin_oji.so .
```

Are you using 64 bit Ubuntu? I read this Java may be used with the 64 bit OS but I couldn't get it to work. Sun is supposed to soon release their 64 bit version.

---

### Post by Kleenux on 2008-07-14
Hi raptor, I'm using the 32 bits version.

I'd like to underline the fact that neither the previous Java plugin (1.6_0_7 I think) nor the new one work with FF3. WHile I never had a problem with FF2.

The libjavaplugin_oji.so lib is even copied into the plugins dir... that should work.
Do you guys have no problem using the Java plugin in FF3 from Ubuntu?

---

### Post by tuxxy on 2008-07-14
Not at all on 64bit,

/usr/lib/jvm/java-gcj/jre/bin/java works fine for me


you could try Opera also if no luck, what sites specifically are you having problems with?

---

### Post by Kleenux on 2008-07-14
> **tuxxy said:**
> what sites specifically are you having problems with?
:confused: well I'd say all sites with Java applets :confused:

---

### Post by avtolle on 2008-07-14
Since you are on 7.10, you might need to create a symblolic link to get the plugin working. And, now that I've said that, I will also tell you that I can't find my link on how this is done. :-(

---

### Post by raptor2552 on 2008-07-14
Is Java enabled in your preferences? 

I suppose it doesn't really matter where you put the link or library. My point was that if library or link is in the firefox-addons/plugins directory you should not have to mess with it after upgrading firefox. I'm at firefox 3.0.1 and Java works fine

---

### Post by tuxxy on 2008-07-14
```
sudo ln -s /usr/lib/java/dir/plugin.so /usr/lib/firefox/plugins
```

Where you would replace /usr/lib/java/dir/plugin.so with the location of **your **java

If no luck essentially just make sure that you have the file libgcjwebplugin.so in your /**usr/lib/mozilla/plugins/** ** /usr/lib/firefox/plugins/** **/usr/lib/firefox-3.0/plugins/** folders.  Remove any plugins that may be causing a conflict so other ones with "java " in the title.  

Run this in the terminal

```
sudo update-alternatives --config java
```

Select whichever number is listed by 

```
 /usr/lib/jvm/java-gcj/jre/bin/java 
```

Now your firefox should display the plugin by entering **about : plugins** into the browser.  

You should be using the gcj java plugin now and if its not working then you still either have conflicts in the plugins folder or you have still not got the plugin in the correct folder.

Good Luck

---

### Post by Kleenux on 2008-07-14
> **raptor2552 said:**
> Is Java enabled in your preferences? 
I'm at firefox 3.0.1 and Java works fine

Yes it is enabled.
FF 3.0.1 ? Mine is 3.0 (Ubuntu) ; are you under windows?

> **tuxxy said:**
> ln -s /usr/lib/java/dir/plugin.so /usr/lib/firefox/pluginsActually I have a copy of the plugin in the /usr/local/firefox/plugins dir (FF3).

> **tuxxy said:**
> /usr/lib/jvm/java-gcj/jre/bin/java
java-GCJ (google code jam :-) plugin works, after installation, thanks, but I want to use the plugin from Sun...

---

### Post by tuxxy on 2008-07-14
Glad to see it works fine now, why do you want to use the Sun plugin if gcj is fine?

If you do want to change it then repeat the process and do 

```
sudo update-alternatives --config java
```

Select your Sun, then make sure the plugin is in firefox pluginfolder, think for Sun its title is JAVA and again you may have to delete gcj one due to conflicts.

---

### Post by Kleenux on 2008-07-15
> **tuxxy said:**
> why do you want to use the Sun plugin if gcj is fine?
I didn't say it works *fine*. It was rather a test to see if the plugins is recognised. It is. I had problems in the past with the gcj plugin, moreover Sun developed a brand new plugin for FF3 "better and faster", this is why I want this new one.
Note, again, that even the old FF2 Sun Java plugin that used to work with FF2 doesn't work (not detected) in FF3.

> **tuxxy said:**
> If you do want to change it then repeat the process and do 
sudo update-alternatives --config java

The new GCJ plugin (installed from synaptic) doesn't show in the list... 
```
There is only 1 program which provides java
(/usr/lib/jvm/java-6-sun/jre/bin/java). Nothing to configure.
```

Probably you meant "update-alternatives --config mozilla-javaplugin.so", that still show the same```
  Selection    Alternative
-----------------------------------------------
    1    /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so
*+  2    /root/jre1.6.0_10/plugin/i386/ns7/libjavaplugin_oji.so
```
By installing the plugin directly in the FF plugins folder, it should work (without worrying about alternatives). Even after cleaning completely the java and plugins alternatives, redo a clean install, it does not work. I think it is maybe a problem with FF3?

---

### Post by Kleenux on 2008-07-15
Ok it works, at least the default Sun plugin...
This is what I did to get it working

- removed completely the default firefox (as there is no package for FF3, and don't want to wait for 107 years before it is available) ; new one is in /usr/local/firefox
- removed completely any sun jre
- removed the many alternatives using the command, then using the other command: rm!

- reinstalled the default jre (1.6.0_03 unfortunately... don't know how to install the 1.6.0_10 over the old one *cleanly* when there is no package)
- created an alternative for firefox-javaplugin.so (and not the other mozilla-javaplugin.so, coming probably from ancient times)

So the Sun version (default) works. I guess the new (1.6.0_10) could not work because it uses the other (03) dyn libs that have not been properly installed. And here I'm stuck, how to install the new jre without a debian package? this is the question...

---

### Post by alidiot on 2008-08-04
PROBLEM: Firefox 3 JRE6 bug on Debian

SYMPTOM: applets do not appear/are not fetched after installing JRE6 or after creating symlink in plugins folder to existing JRE

attiladehun on the BLAG forums wrote:

>  
"The latest Java 6 from Sun requires compatible libraries to run: compat-libgcc-296. Use either apt-get or the "Add/Remove Software" menu item to install, and java should then function."


see: [http://forums.blagblagblag.org/viewtopic.php?p=25877#25877](http://forums.blagblagblag.org/viewtopic.php?p=25877#25877)

If this does not work for you try installing libstdc++5

see: [http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6542512](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6542512)

>$ sudo apt-get install libstdc++5 

or via Synaptec Package Manager

This will also ask to install the required gcc-3.3-base files

Should work with JRE6, not required for earlier JRE's
(see Sun article above)

---

### Post by Kleenux on 2010-05-08
Thanks

---

