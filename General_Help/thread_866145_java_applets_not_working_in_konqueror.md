---
title: "java applets not working in konqueror"
date: 2008-07-21
forum: General Help
---

### Post by r.stiltskin on 2008-07-21
I'm running Ubuntu (not Kubuntu) Hardy but have also installed
konqueror, konq-plugins and konqueror-nsplugins.  In Settings/Configure Konqueror/Java and Javascript, Java is enabled, and about:plugins shows Java Plug-in KJAS for Konqueror, but still Java applets fail to load.

Any ideas?

---

### Post by glurks on 2008-07-21
Same problem here. Neither konqi nor firefox load java applets.
They both show the plugins in about:plugins.

---

### Post by glurks on 2008-07-21
For firefox the following helps:

cd /usr/lib/firefox-addons/plugins
ln -s /etc/alternatives/firefox-javaplugin.so

What is the equivalent thing for konqi?

---

### Post by glurks on 2008-07-21
The link also helps for konqueror. One needs to log out to reload the browser, I guess.

---

### Post by r.stiltskin on 2008-07-21
Java in my Firefox-3 "just works" - I didn't have to do anything special.

I still can't get Java to work in my Konqueror.  In /etc/alternatives, the only thing I have relating to a java plugin is xulrunner-1.9-javaplugin.so, so I tried creating a link to that in /usr/lib/firefox-addons/plugins; I also tried creating links to /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/plugin/i386/ns7/libjavaplugin_oji.so there and also in /usr/lib/firefox/plugins and in /usr/lib/mozilla/plugins.  None of these helped.

I think the problem may be that in Konqueror's about:plugins it gives "kjavaappletviewer.so" as the name of the Java Plug-in but my default JVM is sun 1.5 -- but I don't know what to do about that.


PS: I also wasn't able to get java working in Firefox-2; that's why I installed Firefox-3.

---

