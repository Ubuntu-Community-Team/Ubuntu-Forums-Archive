---
title: "Why is Java failing so badly on Linux?"
date: 2008-11-30
forum: General Help
---

### Post by kaldor on 2008-11-30
I am finally to the point of possibly switching to Solaris or something besides Linux. Java is causing too many problems for me. I try to play a java based game, what happens? Either it will not load, it crashes the browser, or it kills sound on everything until I reboot. I try it in another browser, it loads, but I am unable to type anything. This can be extremely frustrating.

How can I fix this? I am almost better off without Java at all. I really do not want to switch from Linux. I love Ubuntu and Linux as a whole, but Java is really getting to me.

---

### Post by taurus on 2008-11-30
How did you install java?  

Are you sure it's java and not flash?  

Why don't you post the site so others can check it for you?

---

### Post by binbash on 2008-11-30
what is the ouput of : 

update-java-alternatives -l

---

### Post by kaldor on 2008-11-30
It is Java, not flash.

I installed Java using the download link on the Java website ([http://javadl.sun.com/webapps/download/AutoDL?BundleId=25051](http://javadl.sun.com/webapps/download/AutoDL?BundleId=25051))

My girlfriend has this same problem as well. She is running openSUSE.

Runescape runs on Java. You will not be able to really see what I am talking about unless you sign up/already have an account there. It crashes firefox, screws up the sound, and sometimes refuses to load at all.

The other thing I use Java for is an FTP for a server. Sometimes I am unable to alter files (cannot type) which requires a reboot most of the time.

---

### Post by kaldor on 2008-11-30
> **binbash said:**
> what is the ouput of : 

update-java-alternatives -l

```

michael@laptop:~$ update-java-alternatives -l
java-6-sun 63 /usr/lib/jvm/java-6-sun

```

---

### Post by binbash on 2008-11-30
Ok, first of all, runescape SUCKS at firefox with java.I agree with this part.You will see  white screens often.I use opera when i am playing runescape.I dont have a single problem with opera + java at runescape.

I always prefer opera when i am playing with java.

---

### Post by kaldor on 2008-11-30
That is what I do. I use Opera for Runescape when firefox is not working. About 50% of the time I try to play, I cannot type. My girlfriend also has random logouts and random freezes on Runescape in Opera as well.

Also, why is it that when you open a new tab or minimize a window, I get a white screen in Runescape?

---

### Post by binbash on 2008-11-30
Ok lets talk runescape problems first.

First of all i strongly suggest using firefox 3.1b , i am getting less problems, faster speed etc.
When you do alt tab at firefox while playing runescape HD, i was getting damn whitescreens.But at opera i do not get this.I never see whitescreens when opening a new tab or new window or minimize (maybe once max)

For typing problem.I was also getting this at login screen at hardy.I know what you feel : ) , i was right clicking outside of java, playing with options a little (resolution etc) then it enters the text.I dont know a solution for this but right clicking outside the java solve my text problem %95 of time.




PS : I was playing runescape 4 months ago.The experiences i wrote here was based on that date.I was playing runescape HD , fullscreen

---

### Post by kaldor on 2008-11-30
This seems like it may have helped the Opera problem. If I find any more problems, I will post here. Thank you for the help :)

---

### Post by Tobster on 2008-11-30
It best to use Synaptic Package Manager for installing things like Java.  Personally I try and you Synaptic as much as possible for ease and it is very rare that you need to go outside the Synaptic set-up for installing software.  I think I had to do it twice this year once for installing X2 which I brought from Linux Games Publishing and when I installed Second Life...

To be honest I was once thought that I knew everything about computers but I was sadly mistaken.  I knew everything about Microsoft Windows and Microsoft product... I look back and I realize that I did not know about computing I knew about Microsoft.  To understand computing is to understand Linux, BSB and any other UNIX type system,  To know computing is to know about the Debian, Red Hat standard (as well as Microsoft) To know about computers is to have full knowledge of KDE and GNOME X-Windows Systems (Not forgetting Redmond - Windows and Aqua - Apple)

Sadly in Colleges they only teach Windows - it make you wonder if they really know about computing....

---

