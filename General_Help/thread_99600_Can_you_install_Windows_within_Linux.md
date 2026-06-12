---
title: "Can you install Windows within Linux?"
date: 2005-12-05
forum: General Help
---

### Post by BabaFree on 2005-12-05
I remember reading an article sometime ago about installing windows within linux using the windows cdrom.  I am looking for a program that could do that.  What I need to do is run Microsoft Frontpage.  Crossover won't do it so I'm left hoping that this is an option because I really don't want to have to dual boot again.    
Thanks and God Bless,
Baba

---

### Post by Bachstelze on 2005-12-05
VMware is what you're looking for :)

---

### Post by soulestream on 2005-12-05
[http://ubuntuforums.org/showthread.php?t=84275](http://ubuntuforums.org/showthread.php?t=84275)

soule

---

### Post by Anomaly on 2005-12-05
I dont see anything wrong with dualbooting except (in your case) you would probably have to take ubuntu off first.

---

### Post by mherring on 2005-12-06
[QUOTE=Anomaly]I dont see anything wrong with dualbooting except (in your case) you would probably have to take ubuntu off first.[/QUOTE]

---except that he doesn't WANT to dual boot.  (I DREAD jumping over to Win2k since it takes SOOOOO long to come up.)

---if you install Windows on a different drive, then you can make it the first, and then configure grub.conf so it can still find the Ubuntu.  Maybe easier to re-install....;)

While we are offering more advice than the OP asked for....;)
     Dump Frontpage and use one of the web authoring tools that works natively in Linux.  I like Bluefish.  For GUI---look at NVU.
     Dont rule out running two computers and a KVM switch.  You can put together a CPU pretty cheap---especially by scrounging some used parts.

---

### Post by BabaFree on 2005-12-07
[QUOTE=mherring]
While we are offering more advice than the OP asked for....;)
     Dump Frontpage and use one of the web authoring tools that works natively in Linux.  I like Bluefish.  For GUI---look at NVU.
 [/QUOTE]

I think I'm going to go this route.  I absolutely did not like to reboot everytime I wanted to work on webs.  I've never used Bluefish but I've been tinkering for the last few days and am starting to like it.  Thanks a lot for the advice.
Baba

---

### Post by pizzach on 2005-12-07
Off topic, but but this bugged the heck out of me with the boss I had worked for.  Did the word "Webs" actually catch on in the web developer world?  Or is it only a Frontpage excentric thing still?  For some reason the word always rubbed me wrong whenever I heard it.

---

### Post by pbrockway2 on 2005-12-07
[QUOTE=pizzach]Off topic, but but this bugged the heck out of me with the boss I had worked for.  Did the word "Webs" actually catch on in the web developer world?[/QUOTE]

Well bugged.  If the word is catching on let's stamp it out.  What are
being authored are component parts of *a* web.  Sites maybe, not webs.

Bluefish is nice.  I've been using Eclipse recently with various plugins
for php etc.  Good if you to integrate java or C/C++ with your pages.
Or Kate.  Whoops! ... wrong forum!

---

### Post by BabaFree on 2005-12-07
[QUOTE=pizzach]Off topic, but but this bugged the heck out of me with the boss I had worked for.  Did the word "Webs" actually catch on in the web developer world?  Or is it only a Frontpage excentric thing still?  For some reason the word always rubbed me wrong whenever I heard it.[/QUOTE]

Honestly, It bugs me too, but I learned Frontpage out of a book that used the word.  Thanks for pointing it out to me so I don't get in the habit of using it.
Baba

---

### Post by brim4brim on 2005-12-07
VMWare does not work well from my experience with it and SuSe about a year ago, it was just horrible and wouldn't boot.  Also although windows users get the benefit of a GUI installer using the MSI installer, they don't provide the same for Linux which bugs me.  If you pay the same amount as the windows user you should get the equivalent application or in other words it should have an installer for it.

---

### Post by hedone on 2005-12-07
I have VMWare 5.0 installed. It runs winsdows almot better then if u install them normali on harddisk... 

anyway... i use vmware only for bank aplications. my bank is still windowsed!!! :(

for every other software i did find suitable (in many cases even batter) in linux... and as far as i'm consured... as soon my bank gets me some software for linux i'm gonna uninstall VMWare...

And yes... guys... VMWare is serius aplication from 5.0 on!!! older versions was maybe a little bugy... but 5.0 works realy ql!!! when did u last time see win XP pro runing on 44 MB ram??? ;)

---

### Post by pizzach on 2005-12-07
[QUOTE=BabaFree]Honestly, It bugs me too, but I learned Frontpage out of a book that used the word.  Thanks for pointing it out to me so I don't get in the habit of using it.
Baba[/QUOTE]


Sorry.  I was trying not to sound like a jerk.  I'll give you a bit of a lowdown on webpage design programs in a nutshell from my experience:

**Frontpage:**
It's okay.  New versioner versions are so much more powerful than they used to be.  It's a good program for beginners in that it works a lot like the standard word processor.

**Dreamweaver:**
Powerful.  Can be a bit difficult to handle.  It felt like it's made for people who don't mind playing with the code.

**Nvu:**
Still feels a bit overly young to me.  But for general layout, it does the job.  Last time I tried it it was still a bit buggy even though it was at 1.0.  It might be the best transition linux transition program though given that you're coming from front page.

**Any old text editor that does syntax highlighting, has tabs, and can have green text on white:**
My favorite.  :)

I just looked at some snapshots of Bluefish.  It's actually pretty nice looking.  I'll have to try it next time I'm building a webpage. [To the original poster] it has no wysiwyg from what I could see.

Be wary of not learning code. (I have no idea how much or what kinds of things you know.  Stop reading here if this doesn't apply.)  Sometimes it's very helpful for tweaking webpages.  With direct coding a lot of times things come out cleaner and smaller and you can do much more interesting things.  Plus, you're more flexible if you aren't dependent on a program.  If you know exactly what those little menus and button are doing in wysiwyg things also tend to get a bit less messy.

---

### Post by jliedeka on 2005-12-08
I use VMWare under Red Hat to run Win2K.  The only thing I really need Windows for is TOAD and ocassionally checking out web pages under IE for javascript functionality.

I keep thinking I'm going to hijack some open source java-based DB tool and replicate the functionality I want.  Then I won't really need Windows at all.

I have to use Red Hat at work because it's the only desktop OS supported by VMWare.  Plus, I've been using Red Hat for 8 years so I know it better than the others anyway.  But at home it's all Ubuntu.

---

