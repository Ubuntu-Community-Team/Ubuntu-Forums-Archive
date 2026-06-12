---
title: "A sad story of a hp pavilion dv6000 user :("
date: 2006-12-18
forum: Hardware &amp; Laptops
---

### Post by emperon on 2006-12-18
Hello,

Recently I bought an hp pavilion dv6000 with AMD 64 x 2 core duo processor, broadcom wirless driver and nvdia graphics card. I have been using linux for the last 4 years. And ubuntu for 1.5 years. However I am very much disappointed of the compabilitiy of my hardware with linux. Prolly I shouldnt have bought this machine at first place.

When I got my machine I turned it on. The first thing I have done was removing windows. I put my edgy 32 bit CD then what, it didnt boot. I was shocked. I was expecting some issues say for graphic card but from that beginning... After digging the issue I figured out noapic boot option fixes the problem. Well fine for me. I went that way. I installed ubuntu without a problem.

I booted up my machine. I installed nvidia drivers. Beryl. wow it worked out of box. Then I figured out I have to use ndiswrapper for broadcom wireless. I said well no problem. I installed my driver and it worked fine for 5 min. Then it conflicted with nvidia. After digging I learned that there is an compability with wirless smp support and nvidia. This issue fixed in next kernel starting with 2.6.19. Again I was not desperate. ok I dont have to use wireless at all.

Finally I realized my headphone jack is not working as well as my mic, I learned this has been fixed in alsa 1.0.13. I downloaded the source code compiled it. And it rendered my system completely useless. I checked the log files etc, not a single error I could see.

I said hmm... May be I should try fiesty even if it is alpha, I take responsibility for any breakups. Well of course things were not easy.  Fiesty couldnt recognize my video card at all. It acknowledged it as vesa which so slow that it unusuable for me.

Well these are very painful moments for me. Tomorrow morning I have make a reinstallat'on may be 6 th time this week.

I just wanted to share...

Update : Finally I upgraded my kernel to 2.6.19.1 and most of the issues I mentioned above has been resolved :)

---

### Post by mikewhatever on 2006-12-24
It is not so sad after all. What has not been resolved?

---

### Post by Grayscale on 2006-12-26
Hey, I have one of these laptops...how did you eventually get the mic and headphone working?  By compiling alsa or upgrading your kernel?  I was planning on recompiling my kernel eventually, maybe I can fix it then.

---

### Post by kwilliam on 2006-12-27
I am going to buy a laptop for college, and the HP dv6000t is my current top choice. (I will go with the Intel Core 2 Duo chip, rather than AMD.)  How much did you get to work?
[LIST][*]I absolutley HAVE to have wireless internet and Beryl.
[*]I would LOVE working microphone, webcam, and sleep/hibernate.
[*]I would like (but don't really need) working headphone jack, HP Mobile Remote Control, and bluetooth.[/LIST]

The model I'm considering uses an Intel(R) PRO/Wireless 3945ABG Network w/Bluetooth, which I believe will work with Linux.  (At least the version without bluetooth works according to cepes.org.pe/jaime/dv8000t.html)  I plan on studying engineering, and will probably dual boot Windows and Kubuntu, because I'm a KDE fan.

---

### Post by emperon on 2006-12-27
I have only compiled 2.6.19.1 without interfering alsa. After that, headphone jacks and mic jacks was working.

Currently some problematic issues with 2.6.19.1:
- Hibernate does not work 
- Suspension works fine mostly, but after I resume , I am losing sound.
- When I put the headphone jack on, the speakers do not mute. I have to mute them manually. But this is not a major issue.
- I still have to use ndiswrapper for wireless, but works fine even with SMP and NVidia
- Battery meters is inaccurate , but not a major issue for me.

Other than these, everything looks fine, wireless and networking are fine, Nvidia with beryl is fine, sound and video is fine. Performance is fine.

P.S, I followed the guide for kernel compilation guides in ubuntu forums which did not work for me. I had to specify initrd option while making the kernel

---

### Post by comfurtn on 2007-01-03
As an HP dv6000 series owner myself, I'd say that these laptops are terrific in their own right.  Making everything work the way you want it to with Ubuntu is a bit of a trick though. ](*,) 

Check out the wiki page that I've helped with.. it has some good tips and tricks to get these laptops up and running!

[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29]("https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29")

---

### Post by oobuntoo on 2007-01-12
> **comfurtn said:**
> As an HP dv6000 series owner myself, I'd say that these laptops are terrific in their own right.  Making everything work the way you want it to with Ubuntu is a bit of a trick though. ](*,) 

Check out the wiki page that I've helped with.. it has some good tips and tricks to get these laptops up and running!

[https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29]("https://wiki.ubuntu.com/hp_dv6000_series_%28dv6116eu%29")


I have hp dv6000t and managed to get my headphone jack to work by following tips from above link.
 
However, alsa verion 1.0.13 gives me two volume controllers in my mixer; one for laptop speakers and one for headphone jack. They are independent of each other, which means both headphone and laptop speakers work at the same time. I have to manually turn down volume in the mixer for laptop speaker when I want to use headphone only. The physical laptop volume and mute buttons only work for headphone.

Alsa verion 1.0.14rc1 works like it's supposed to, ALMOST. It does automatically switch off laptop speakers when I plug in my headphone, but the mute button on the laptop only works for headphone and not the laptop speakers and the light on it is glowing red instead of  blue.

Anyone else has these issues?

---

### Post by emperon on 2007-01-12
Alsa 1.0.13 in fiesty works fine. Just hold on a couple of months.

---

### Post by chinthaka on 2007-01-21
I also have the same laptop and my mic is also not working. I installed alsa 1.0.14 RC2 but still my mic is not working. 
Any other clues to get this fixed? Since I use skype heavily, this had caused me to login to windows whenever I need to make a call ](*,)

---

### Post by azelter on 2007-02-02
I also have a dv6000. All works well in Feisty except the webcam and mic. Did anyone manage to solve the mic problem yet?

---

### Post by teaker1s on 2007-02-21
hi guys, feisty and latest bios cured most of my 6116eu issues and hopefully latest xorg on way will cure the last hurdle

---

### Post by fulio on 2007-08-17
Hi i also have a Hp pavilion dv6000 and im having so much problems with it at the moment. i went on mIRC #ubuntu & #ubuntu-effects. they tryd there best to solve my problems but still no Help.

The problem.. ---> ubuntu cannot connect to the internet wirelessly. i have to connect through the internet using a wired connection. i configured everything and still doesnt work. 
my 2nd problem. my nvidia drivers, well people on #ubuntu said it can be my bios.. Well this is what happens. when i try to enable my desktop effects and click enable it says "Desktop effects could not be be enable" i was like wth.. and the top right corner it says "System restart required" so i reboot.And it boots ; then i get a "Failed to start the X server. Which i have to go back to vesa agn. i also install the lastest driver. i just dont know whats the problem any Help pleas.e.

---

