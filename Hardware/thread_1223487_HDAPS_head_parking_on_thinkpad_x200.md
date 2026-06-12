---
title: "HDAPS head parking on thinkpad x200"
date: 2009-07-26
forum: Hardware
---

### Post by desmane on 2009-07-26
hi folks, 

I know this is a big one and there is lots of resources on how to install the hdaps and smapi head parking stuff. 

I just dont get it to work, I am not very gifted in compiling kernels, applying patches and stuff. 

Using ubuntu since 7.04, but having a thinkpad (and being a bit clumsy) without headparking makes me kinda nervous and this morning I was like "do I need to go back to windows cause of my hardware?" (i bought ibm because of linux support too!)

I love linux, but now I am just like, is it safe to suspend to ram for many hours with my laptop on the go? Does ubuntu do head parking before going to sleep? It runs much cooler on windows, too.

[B]okay, I am loosing the thread here, the actual question: 
how does this work: [http://www.thinkwiki.org/wiki/HDAPS](http://www.thinkwiki.org/wiki/HDAPS)
on ubuntu 9.04 jaunty with 2.6.28-14-generic[/B]

Can someone give some advice on which steps I have to go for and which not? What is allready in the kernel, what patch do I need to apply?

If I get it to work with your help, I am so going to write an ubuntu x200 jaunty jackalope howto as a thank you to the community :)


I really hope I get it to work with your help, the x200 is such an wonderful machiny, hope some others will benefit from this!! THANKS!!

---

### Post by desmane on 2009-07-27
nothing?

---

### Post by rCXer on 2009-07-27
I just got this working yesterday on a T43 thinkpad using [these instructions](http://www.thinkwiki.org/wiki/Installing_Ubuntu_9.04_(Jaunty_Jackalope)_on_a_ThinkPad_T61#Enabling_Active_Protection_System). It took me several hours and I had to change/rebuild hdapsd.  Although It's for a T series laptop it might work on your computer as well.  

What version of the kernel are using? You no longer have to patch the kernel if you have version 2.6.28 or later.  All you have to do is add a module as in the link I posted.

---

### Post by desmane on 2009-07-29
that worked, thanks for pointing me in the right direction ;-)

the applet doesn't react though. If I issue the following command, i get this error

```
$ sudo hdapsd -d sda -s 15 -a -v -y 
protect_file: /sys/block/sda/queue/protect
threshold: 15
read_method: poll-sysfs
open(protect_file): No such file or directory

```

hdaps-gl and hdaps-pivot are working. 

here it says, 

[http://www.thinkwiki.org/wiki/HDAPS#How_to_install_the_driver](http://www.thinkwiki.org/wiki/HDAPS#How_to_install_the_driver)

> It doesn't whitelist them (you have to edit hdaps_init() in drivers/hwmon/hdaps.c to include a line like HDAPS_DMI_MATCH_LENOVO("ThinkPad T60")) 

but how do I whitelist them (and what... and where?? :confused: )

mmmmmhh

uname -r --> 2.6.28-11-generic

any idea? thx!

---

### Post by desmane on 2009-07-29
figured it out, added 

[https://launchpad.net/~jonasped/+archive/ppa](https://launchpad.net/~jonasped/+archive/ppa)

to my sources.list and reinstalld hdapsd

---

### Post by desmane on 2009-07-30
no my suspend to ram is broken. I followed the instructions closely, do you now why this happens?

---

