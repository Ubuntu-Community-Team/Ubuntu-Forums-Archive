---
title: "Java still installed but not working after upgrade"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by OriTheEep on 2009-11-08
I refer to the firefox plugin (Sun Java 6) installed with the Ubuntu restricted extras.

This was working in 9.04 but hasn't since the upgrade to 9.10.

It does not even appear in the (Tools/Add-ons) list of Plugins in Firefox.

I haven't been able to find that anyone else has already had the same problem solved in this forum. Apologies if I've missed it.

Hope it's something simple!

Thanks :)

---

### Post by Mighty_Joe on 2009-11-09
Did you try reinstalling the restricted package again?  
The Firefox plugin is a symlink to the plugin in the JDK/JRE install.  Check and see if there's a file named "libjavaplugin.so" or something like that in /usr/lib/mozilla/plugins/
If it's not there, you can create the symlink yourself:
```
sudo ln -s /etc/alternatives/mozilla-javaplugin.so libjavaplugin.so
```

---

### Post by OriTheEep on 2009-11-09
> **Mighty_Joe said:**
> Did you try reinstalling the restricted package again?  
The Firefox plugin is a symlink to the plugin in the JDK/JRE install.  Check and see if there's a file named "libjavaplugin.so" or something like that in /usr/lib/mozilla/plugins/
If it's not there, you can create the symlink yourself:
```
sudo ln -s /etc/alternatives/mozilla-javaplugin.so libjavaplugin.so
```

Thanks for the suggestions. It's not there yet, I'm afraid. This is what happened...

Removing then re-installing the restricted package had no beneficial effect on Java (hopefully no detrimental effect elsewhere either!).

Searching for files "libjavaplugin" in the "File System" only picked up two instances of "libjavaplugin_jni.so". One in "/usr/lib/jvm/java-6-sun-1.6.0.16/jre/lib/amd64", the other in "/home/tom/jre1.6.0_13/lib/amd64". These have the same size but different modification dates.

The symlink you suggested I look for did not exist even after trying the code you kindly gave to create it.

Checking, I find that "mozilla-javaplugin.so" does not exist in "/etc/alternatives".

This prompts me to double check with Ubuntu Software Centre where I find that the Java **plug-in** does not show as installed. I am fairly certain that I (eventually) furnished 9.04 with a Java plug-in by installing the restricted package but for 9.10 the plug-in is not, apparently, included. Was it in 9.04 or did I dream that?

Anyway, happy with anticipatory thoughts of a problem solved I asked the software centre to install just the plug-in.

Apparently, there are "Package dependencies" to "resolve". The error dialogue continues, "This error could be caused by required additional software packages which are missing or not installable. Futhermore there could be a conflict between software packages which are not allowed to be installed at the same time." and gives "sun-java6-plugin" as the only available detail.

Apart from a vague notion that perhaps this could point to my being stuck between two versions of Java 6, I am at a loss and must pass the ball back to more experienced hands.

Thanks again :)

---

### Post by Mighty_Joe on 2009-11-10
I take it you are running 64-bit Ubuntu?  

Did you install Java via the repositories or did you download the .bin file from java.com?

---

### Post by OriTheEep on 2009-11-10
> **Mighty_Joe said:**
> I take it you are running 64-bit Ubuntu?  

Did you install Java via the repositories or did you download the .bin file from java.com?

I am indeed running 64 bit Ubuntu.

As far as my, admittedly not terribly reliable, memory has it, I finally managed to install Java via the restricted extras package. However, I do also remember a terrible load of faffing about trying to get everything to work so it is quite possible that .bin files were also involved at some stage.

---

### Post by witeshark17 on 2009-11-10
Have you seen the [ the java security thread?](http://ubuntuforums.org/showthread.php?t=1314202)

---

### Post by Mighty_Joe on 2009-11-11
> **OriTheEep said:**
> I am indeed running 64 bit Ubuntu.

Little details mattter ;)
Apparently the 64-bit libraries are named differently from the 32-bit.

> **OriTheEep said:**
> 
it is quite possible that .bin files were also involved at some stage.

My wild guess is that the plugin was installed via the .bin and that's why it was not carried over in the upgrade.
In any case, you should be able to identify a file named something like "mozilla-javaplugin" in /etc/alternatives and customize the command I gave you to link it to Firefox.

---

### Post by OriTheEep on 2009-11-11
> **witeshark17 said:**
> Have you seen the  the java security thread?

I have now, thanks for pointing it out! :)

It certainly made interesting reading from the technical viewpoint; learning new things all the time.

I noted the first paragraph of the "how to" with some interest but I don't know enough about the situation to make any further valid comments.

> **Mighty_Joe said:**
> Little details mattter
Apparently the 64-bit libraries are named differently from the 32-bit.



My wild guess is that the plugin was installed via the .bin and that's why it was not carried over in the upgrade.
In any case, you should be able to identify a file named something like "mozilla-javaplugin" in /etc/alternatives and customize the command I gave you to link it to Firefox.

Easy peasy!



Thank you both for the help, as a result of which I know have Java working again.

Still many problems to sort out but I'll get to them one by one in time.

---

