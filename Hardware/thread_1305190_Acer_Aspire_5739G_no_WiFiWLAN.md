---
title: "Acer Aspire 5739G no WiFi/WLAN"
date: 2009-10-29
forum: Hardware
---

### Post by fosron on 2009-10-29
Hey,

After installing Ubuntu 9.10 (wiht Wubi), i have no Wifi, neither LAN. Terminal shows that both of them is discovered by Ubuntu, but i can't connect. There's just loopback interface...
The button for WiFi doesn't work, so i can't enable it... But i think it's somewhere deeper...

WiFi - **Intel 5100 ABG**
LAN - **Atheros AR8131**

And it's weird, that 9.04 works just perfectly...

Some help would be really cool, because all of the info on the net is for <9.10 , and just doesn't work, or doesn't do any difference...

---

### Post by fosron on 2009-10-30
Bump. Still can't do anything about it...

---

### Post by fosron on 2009-10-30
sry for this , but i really need some help!

---

### Post by gecko1337 on 2009-10-30
I had the same problem as you, and for me I did the following and now it works just fine!:D

```
sudo gedit /etc/default/grub
```
you'll find
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
change it to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off"
```
update grub..
```
sudo update-grub
```
and restart

---

### Post by logically on 2009-11-02
To Fosron : 

Did the GRUB-trick from gecko1337 work for you? I tried installing Ubuntu 9.10 this weekend and ended up with the same problem that you encountered. I would like to try installing again, but would like to hear if this worked for you first? :)

---

### Post by mitch_feaster on 2009-11-03
> **logically said:**
> I would like to try installing again, but would like to hear if this worked for you first? :)

I can vouch for the disabling acpi method. I (not surprisingly) had the same issue on my 5739g and it (not surprisingly) worked for me too.

The problem with disabling acpi is that, well, you don't have acpi anymore! You can't do things like get battery status, shut the machine off without actually pushing the button, etc. (Anyone reading this thread contemplating a 5739g: I love mine, don't let these issues hold you back! They'll be fixed soon enough I'm sure.)

Does anyone know any other way to fix this? I would sure like to have my acpi back...




Here's an apparently problematic snippet of my dmesg:

```

[   46.790662] iwlagn 0000:05:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x0000008C
[   46.805808] iwlagn 0000:05:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x0000008C
[   46.820965] iwlagn 0000:05:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x0000008C
[   46.837920] iwlagn 0000:05:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x0000008C
[   46.853066] iwlagn 0000:05:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x0000008C
[   46.868212] iwlagn 0000:05:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x0000008C
[   46.883357] iwlagn 0000:05:00.0: MAC is in deep sleep!.  CSR_GP_CNTRL = 0x0000008C
[   46.894517] iwlagn 0000:05:00.0: Failed to init APMG
[   46.894564] iwlagn 0000:05:00.0: PCI INT A disabled
[   46.894599] iwlagn: probe of 0000:05:00.0 failed with error -110


```

There are a bunch of other acpi-related messages before this but they fall off the buffer because there are about 1500 lines of the above "deep sleep" message. Any ideas?

---

### Post by tkarch on 2009-11-03
i did what gecko1337 said to do... worked perfectly. only took a second... thanks for the help. would you happen to know how to fix the fingerprint scanner.  I'm very new to ubuntu, and laptops for that matter.

---

### Post by logically on 2009-11-04
I installed Ubuntu 9.10 yesterday and applied the acpi-fix! It worked right away and i got lan and wlan up and running. A bit sad that we loose the ability to see battery capasity, but as mitch_feaster said .. "They'll be fixed soon enough I'm sure." :) 

A couple of things that also would be great to have working is the battery-saver button on the right top-side. Does anyone know how to configure this one?

---

### Post by mitch_feaster on 2009-11-04
> **tkarch said:**
> would you happen to know how to fix the fingerprint scanner.

First of all, welcome to Ubuntu. Second, I got my fingerprint scanner using [fingerprint GUI]("http://www.n-view.net/Appliance//fingerprint/downloads.php").

Installation directions:
[LIST=1]
[*]Download the latest [fingerprint GUI]("http://www.n-view.net/Appliance//fingerprint/downloads.php") tarball (I'm using 0.12) ([direct link]("http://www.n-view.net/Appliance//fingerprint/fingerprintGUI-0.12.tar.gz")).

[*]Open a terminal and 'cd' to wherever you downloaded the file
Example:
```

cd Downloads

```
[*]Extract the tarball and enter the directory
```

tar xf fingerprintGUI-0.12.tar.gz
cd fingerprint-0.12

```
[*]Quickly install some dependencies
```

sudo apt-get install libfprint0 libfakekey0

```
Note: there's one more dependency, it's either libqca2-plugin-ossl, or libqca2. Try the first one first.
[*]You're almost there! Read the developer's install directions for configuring PAM. They're in a file called "Install-step-by-step.pdf" in the fingerprint-0.12 directory and are fairly well written. The only thing I had to do differently was copy all my acquired fingerprint data (after Step 2 "Acquiring Fingerprints") to my root user's home directory:
```

sudo cp -r ~/.fingerprints /root/

```
[/LIST]
I think I covered everything I did... Let me know if works. Good luck!

---

### Post by Gintautas on 2009-11-16
Hello everyone,

I've been having the same problem with WiFi as everybody else on this thread and fixed it with the acpi=off solution.

As we all understand, disabling acpi is not a permanent solution as it disables some quite useful features of your laptop. Therefore I would like to know is there anything done about this issue? I mean, will Acer Aspire 5739G users be able to load their machines with Ubuntu 9.10 with acpi and WiFi together?

Thank you in advance,
Gintautas

---

### Post by mitch_feaster on 2009-11-22
> **Gintautas said:**
> Therefore I would like to know is there anything done about this issue? I mean, will Acer Aspire 5739G users be able to load their machines with Ubuntu 9.10 with acpi and WiFi together?


Looks like there was something being done. I just compiled the latest ubuntu kernel (2.6.31-16.51 at the time of this posting) and everything (wifi, wired, **acpi**, etc.) worked great! It's nice to not have to actually push the button to turn this thing off anymore :-)

I followed [these]("http://blog.avirtualhome.com/2009/11/03/how-to-compile-a-kernel-for-ubuntu-karmic/") instructions for compiling the latest kernel. Despite the fact that it's a well-written tutorial, compiling kernels is not for the lighthearted. Just wait for the next kernel update if you're not up to it. It shouldn't take long (can anyone find a karmic kernel roadmap?)

---

### Post by wagaboy on 2009-12-01
Thanks for the quick solution ! But, having acpi off has some serious side effects:
1. Can't turn off the laptop without hitting the power button. 
2. Can't use the trackpad lock. It stops working when "acpi=off" is added to the config. This is a bit annoying while typing when your palm touches the trackpad. 

Also, did anyone manage to get multi-touch on trackpad working ? I tried ```
synclient -m 100
```, and it registers just one click. Multitouch works fine on Windows7.

---

### Post by ram130 on 2009-12-02
Thank god Im not alone!! Since everyone has the same laptop(I believe we all got it from the same site lol) Can someone please tell me if you have any problems with your WIFI signal in both Ubuntu & Windows 7? My problem is that  I cant connect to my router with just a few meters away and one wall behind. Yet my  T mobile G1 phone connects find with 1bar and the laptop has 4 bars out 5. Anyone?

---

### Post by wagaboy on 2009-12-02
> **ram130 said:**
> Can someone please tell me if you have any problems with your WIFI signal in both Ubuntu & Windows 7?

It works fine for me on both OSs. In fact, it manages to detect all access points in 20 yard(=20 mtrs ?) radius. I know because it lists my neighbours' wireless networks.

---

### Post by ram130 on 2009-12-03
> **wagaboy said:**
> It works fine for me on both OSs. In fact, it manages to detect all access points in 20 yard(=20 mtrs ?) radius. I know because it lists my neighbours' wireless networks.


I think mine could be faulty. It detects everything perfectly  but it wont connect within a room to my wireless network. Even with 3-4 bars only connects when I am right next to the router. You got any connecting problems like this?

---

### Post by wagaboy on 2009-12-03
> **ram130 said:**
> You got any connecting problems like this?
Nope. Wireless works fine.

---

### Post by ram130 on 2009-12-04
> **wagaboy said:**
> Nope. Wireless works fine.
 
I guess I am a alone on this one, sending it back for repair. Hopefully they don't take one year.

---

### Post by mjreged on 2009-12-05
Hey Man, you are not alone, I also have problem with this laptop. It only connects to the router if i am 3 feet away from it. Otherwise it drops connections.  So far i spoke to the technical support at acer and they are giving me a run around.  They claim that it's ISP problem.  What a bunch of crap.  It must be defective.  Any tips on how to convince them that it's a defect and they need to accept my claim for fixing this laptop....

I also want to ask you guys if in your laptop; does the CPU fan is constantly running even if you computer is idle?
My laptop fan never takes a rest....

---

### Post by wagaboy on 2009-12-05
> **mjreged said:**
> Any tips on how to convince them that it's a defect and they need to accept my claim for fixing this laptop....

I also want to ask you guys if in your laptop; does the CPU fan is constantly running even if you computer is idle?
My laptop fan never takes a rest....

1. Check your laptop on other WiFi networks. If the problem still exists, you can rule out ISP.

2. Fan works fine on Ubuntu9.10 and Win7.

---

### Post by iani on 2009-12-06
Well, I tried the grub recipe on my turbox laptop (a greek brand I think?) and as a result I could no longer boot my fresh installation of Karmic. Then I tried re-installing it on the existing linux partition, and I lost my windows vista installation as well. I am reinstalling Karmic on the whole drive, as I do not miss Vista that much. I am writing this as a warning to to others.  If a Guru would care to comment? 

Thanks 

Iannis Zannos

---

### Post by ram130 on 2009-12-06
> **mjreged said:**
> Hey Man, you are not alone, I also have problem with this laptop. It only connects to the router if i am 3 feet away from it. Otherwise it drops connections.  So far i spoke to the technical support at acer and they are giving me a run around.  They claim that it's ISP problem.  What a bunch of crap.  It must be defective.  Any tips on how to convince them that it's a defect and they need to accept my claim for fixing this laptop....

I also want to ask you guys if in your laptop; does the CPU fan is constantly running even if you computer is idle?
My laptop fan never takes a rest....

  Well what I had to do was adhere to their "so called" steps and be dumbstruck by words like "the recovery will fix it, don't worry" ..even after I did the restore I told them its nothing to do with software and that I am a professional. I even told them I used a boot able Linux CD to troubleshoot the problem to narrow it down. I also mention I had router diagnostic software which said my laptop was only getting "30% signal" while my phone was getting 70% or more, even when they where right beside each other in front of the router. They got me more angry when they said its  ISP related. I had to point out thats its my network whether or not internet is present so its not. Then they said call linksys and see if there is nothing wrong with the router. 

  Trust me; I went through 4 call backs, 4 steps to troubleshoot by their "rules to fixing a problem" and  a complete recovery where I lost some files I newly downloaded just to convince them. They finally ran out of steps and told me to drop it off by fed ex and that the shipping  & repair will take 8 business days or so before I get it back..hopefully by Christmas.

My advise is to try to convince them by following there steps, tell them you already called your ISP, your router manufacture and who ever else. After that they should take it for repair. *make them feel like they did it all by the book* ..good luck..

---

### Post by vangelisf on 2009-12-13
Hi guys!

I started using Ubuntu some months ago....not much experience but since I come from the DOS age I can follow some instructions if it's needed haha.

I have the very same laptop too (Acer Aspire 5739G) and I still have the acpi issue. With acpi off I have wlan but when I turn it on the wlan card is off!

I saw that post about that working kernel update but unfortunately I still have the problem after one (or two?) kernel updates from the update manager.

Actually I have the 2.6.31-16-generic version of kernel....

How did you guys make wlan work with acpi on?

Any help will be highly appreciated!

Thank you!

---

### Post by wagaboy on 2009-12-13
It was mentioned in one of the earlier posts that upgrading to 2.6.31-16 would fix the problem. I have this kernel version and I am still facing the wireless problem. Is there anything else that I need to do in order to fix the wireless issue. Currently, I have turned off acpi.

---

### Post by sam_sunders on 2009-12-14
> **vangelisf said:**
> Hi guys!

I started using Ubuntu some months ago....not much experience but since I come from the DOS age I can follow some instructions if it's needed haha.

I have the very same laptop too (Acer Aspire 5739G) and I still have the acpi issue. With acpi off I have wlan but when I turn it on the wlan card is off!

I saw that post about that working kernel update but unfortunately I still have the problem after one (or two?) kernel updates from the update manager.

Actually I have the 2.6.31-16-generic version of kernel....

How did you guys make wlan work with acpi on?

Any help will be highly appreciated!

Thank you!


ok i'm like a day old on ubuntu 9.10, so you may already know this, but i was not connecting to the internet, and the only way i could was to type, after the quiet splash, the following;  quiet splash[COLOR=Red] noapic acpi=noirq[/COLOR]

good luck!

[COLOR=Black]however, i still cannot save this setting. i have to do this every time i boot.[/COLOR]
so i guess 9.10 is grub V2, and I have to edit the grub.cfg. in gedit text editor? looking for step by step instructions on how to keep my [COLOR=Red]noapic acpi=noirq [COLOR=Black]setting as a default boot, but no luck yet.


[/COLOR][/COLOR]

---

### Post by markpeers on 2010-01-04
> **ram130 said:**
> Well what I had to do was adhere to their "so called" steps and be dumbstruck by words like "the recovery will fix it, don't worry" ..even after I did the restore I told them its nothing to do with software and that I am a professional. I even told them I used a boot able Linux CD to troubleshoot the problem to narrow it down. I also mention I had router diagnostic software which said my laptop was only getting "30% signal" while my phone was getting 70% or more, even when they where right beside each other in front of the router. They got me more angry when they said its  ISP related. I had to point out thats its my network whether or not internet is present so its not. Then they said call linksys and see if there is nothing wrong with the router. 

  Trust me; I went through 4 call backs, 4 steps to troubleshoot by their "rules to fixing a problem" and  a complete recovery where I lost some files I newly downloaded just to convince them. They finally ran out of steps and told me to drop it off by fed ex and that the shipping  & repair will take 8 business days or so before I get it back..hopefully by Christmas.

My advise is to try to convince them by following there steps, tell them you already called your ISP, your router manufacture and who ever else. After that they should take it for repair. *make them feel like they did it all by the book* ..good luck..

Hi RAM130

My son has just bought one of these laptops and he is having exactly the same problem with the wifi. Did Acer fix the problem we you eventually convinced them that it was a hardware problem? How long did it take to turn around?

---

### Post by ram130 on 2010-01-04
> **markpeers said:**
> Hi RAM130

My son has just bought one of these laptops and he is having exactly the same problem with the wifi. Did Acer fix the problem we you eventually convinced them that it was a hardware problem? How long did it take to turn around?

Acer kept it up and telling me to call back in two days every time I called. I realize they were trying to delay so that I wouldn't get my money back so I decided to call my bank. I filed a dispute and they credited back my account. Acer didn't seem to realize as I called back once more and was told the same thing. During the 8-10th business day, I had found some people with same problem on the site were I purchased it. One person highlighted he fixed the problem by opening up back panel for the wifi and switch the cables around. Another reported the solution worked too. If only I had waited 3 days before I sent it I could have tried it also. I called Acer up and told them what I had found and they noted it. 

  
  Well on the 15th business day (30th of December, it was sent for repair the 9th) they told me that it could not be repaired and offered me a replacement unit. They also said that no more aspire were available and offered me a gateway nv5351(lower spec video card and price). I told them that I would call them back later but didn't. Mainly because that same day I decided to spend a lil a more for a better laptop with HP. I have been an happy customer ever since and my WIFI picks up full bars in my room now. Ubuntu loads up fine with both WIFI and Ethernet working and no video problems. Its perfect and fast. One regret is that the HP I got is 17" but the graphics card more than makes up for it, even better than what the Acer came with, the nvidia 130m.

**Related links: **

[Link to the HP I got..]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01888956&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&product=4041745&lang=en")

Here is where I found the solution, look for the topic "WIFI PROBLEMS CAN BE FIXED, DESPITE AWFUL TECH SUPPORT" [LINK]("http://www.newegg.com/Product/ProductReview.aspx?Item=34-115-675&SortField=0&SummaryType=0&Pagesize=10&SelectedRating=-1&PurchaseMark=&VideoOnlyMark=False&VendorMark=&Keywords=%28keywords%29&Page=2")


Notes:

- Problems keeps coming up with the Acer laptop

- Acer has bad support! and gives you the run around.

- If you get a perfect wifi working with this laptop, great, its a steal for the price but I guess problems had to be some where..even in linux.

---

### Post by markpeers on 2010-01-04
Thanks for the quick reply and for the link to a possible solution. It seems I need to try everything before I resort to Acer support.

---

### Post by ram130 on 2010-01-04
> **markpeers said:**
> Thanks for the quick reply and for the link to a possible solution. It seems I need to try everything before I resort to Acer support.

no problem.. i would go with a  different company that has better support tho...Acer just doesn't respect their customers. Let me know how it goes.

---

### Post by markpeers on 2010-01-05
Well I took the bull by the horns and performed open heart surgery on my son's laptop this evening. 

I simply removed the cover from the bottom that provides access to the disk drive and memory and there was the wifi card sitting next to the drive. I gently removed the white and black wires connected to the wifi card and replaced them the opposite way round. The wires are connected on miniture sockets. After replacing the cover and switching on I held my breath as the machine booted and logged on. The wifi connected immediately with no problem!

After some further testing the wifi can now happily connect to weak signals that were unusable before the modification.

I know have a very happy son and I don't have to do battle with Acer support. :-)

Thanks for the help.

---

### Post by ram130 on 2010-01-06
glad i could help! congrats!! I just wish the solution had presented its self before I sent the laptop off.

---

### Post by fosron on 2010-01-15
Guess what i did to make it work? I freaking deleted the partition of Linux. :) I hate not having normal battery management, no sound (yea, it went off after acpi stuff), and no normal video drivers (the nvidia official drivers for GT130M are piece of junk). And kernel compiling is not the solution, it must be fixed instantly, not with bunch of hacks, damn, i buy a laptop, i want to be microsoft-free guy, and bam, the cardhouse linux goes down like the WTC. Awesome, you know :)

---

### Post by mitch_feaster on 2010-01-15
Well that's no fun at all. In case I was misleading in my earlier post, recompiling the kernel wasn't *that* bad. The instructions on the site I linked to are well written and easy to follow and it takes less than an hour (probably less time than you spent putting windoze on :-)  if you're reformatting everything anyways might as well try the recompile. It's actually kind of fun :-)

---

### Post by ram130 on 2010-01-16
the problem is with the motherboard of the Acer. I have the same card in an HP and it works perfectly. I believe you should try the new 10.04 alpha 2 and see if it works.

---

### Post by fosron on 2010-01-16
> **mitch_feaster said:**
> Well that's no fun at all. In case I was misleading in my earlier post, recompiling the kernel wasn't *that* bad. The instructions on the site I linked to are well written and easy to follow and it takes less than an hour (probably less time than you spent putting windoze on :-)  if you're reformatting everything anyways might as well try the recompile. It's actually kind of fun :-)

Fun no, fun, that's not the priority. I need a working OS and that's all. And at this point, i just freakin' love Windows 7, and yet, it was just ~30 minutes to install, and about ~20 minutes to put drivers on , damn linux install took me 30 minutes and i spent like 4 hours trying to make WLAN work :)) Oh yeah, that's a really good point to use linux, u loose time!!

---

### Post by ram130 on 2010-01-16
> **fosron said:**
> Fun no, fun, that's not the priority. I need a working OS and that's all. And at this point, i just freakin' love Windows 7, and yet, it was just ~30 minutes to install, and about ~20 minutes to put drivers on , damn linux install took me 30 minutes and i spent like 4 hours trying to make WLAN work :)) Oh yeah, that's a really good point to use linux, u loose time!!

buy a mac or install leopard on your laptop ;)

---

### Post by bezz on 2010-01-23
I have just completed a new install. I had to disable acpi as shown in this thread. I then ran update manager and updated all packages. Noticed kernel 2.6.31-17 so I switched acpi back on and it worked.:D

---

### Post by mitch_feaster on 2010-01-23
> **bezz said:**
> I have just completed a new install. I had to disable acpi as shown in this thread. I then ran update manager and updated all packages. Noticed kernel 2.6.31-17 so I switched acpi back on and it worked.:D

I can confirm that 2.6.31-17 works! Oh happy day. My crontab still looks like this just in case there are still issues with the battery indicator widget not updating itself:

```

# m h  dom mon dow   command
10 * * * * cat /proc/acpi/battery/BAT1/state
20 * * * * cat /proc/acpi/battery/BAT1/state
30 * * * * cat /proc/acpi/battery/BAT1/state
40 * * * * cat /proc/acpi/battery/BAT1/state
50 * * * * cat /proc/acpi/battery/BAT1/state
0 * * * * cat /proc/acpi/battery/BAT1/state

```

---

### Post by ram130 on 2010-01-23
yeaaaaaaaaaaaaa :popcorn::popcorn:

---

