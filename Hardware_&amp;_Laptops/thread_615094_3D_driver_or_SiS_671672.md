---
title: "3D driver or SiS 671/672?"
date: 2007-11-16
forum: Hardware &amp; Laptops
---

### Post by pulsifier on 2007-11-16
at risk of sounding like a dope, i found this....

[http://barroslee.blogspot.com/2007/11/release-sis-671sis-672-linux-3d-driver.html](http://barroslee.blogspot.com/2007/11/release-sis-671sis-672-linux-3d-driver.html)

does this mean anything?  i have the m671 chipset, i would like it to function properly, if this is ligit, how can i obtain it?

---

### Post by terrapene on 2007-11-27
Well, I contacted this person and told me that a 3D SIS 672 Driver exist, but only can be offered to costumers. As long as SIS is a Chipset manufacturer, its costumers are mainly motherboard builders, not final users. He kindly sends a feisty 2D SIS 672 driver to anyone who asks for it,  I've tried it on my Fujitsu Siemens V5535 and Gutsy and it works fine!!! . Anyway, you can download it from: 
[http://www.badongo.com/file/5319845](http://www.badongo.com/file/5319845)
[http://www.megaupload.com/?d=OO7FNA7X](http://www.megaupload.com/?d=OO7FNA7X)
[http://rapidshare.com/files/72690205/sis_vga_200807_ubuntu_7.04.tgz.html](http://rapidshare.com/files/72690205/sis_vga_200807_ubuntu_7.04.tgz.html)

All you have to do is moving sis_drv.* to /usr/lib/xorg/modules/drivers/ and modify your Xorg.conf from vesa to sis, by typing:

 $sudo dpkg-reconfigure -phigh xserver-xorg .

---

### Post by pulsifier on 2007-11-30
awesome.  thanks.  i thought everyone was ignoring my post.

---

### Post by Jerzabek39 on 2007-12-01
3D driver is allready done, but where can I get it..?

---

### Post by terrapene on 2007-12-01
It is written, but not available. At least, with this 2D driver you can play movies smoothly. It comes from the same author and it is different from the SIS one supplied with xorg. It has finally 672 support. This is much more than the poor VESA driver we had to use till now.

---

### Post by Jerzabek39 on 2007-12-03
> **terrapene said:**
> It is written, but not available. At least, with this 2D driver you can play movies smoothly. It comes from the same author and it is different from the SIS one supplied with xorg. It has finally 672 support. This is much more than the poor VESA driver we had to use till now.

This is better then VESA driver, but 3D is 3D.. :) Why did they do the driver, when its not available to download..?

---

### Post by VVebbie on 2007-12-10
I just installed this and it works great on Gutsy (Sager NP7250 running M671). Just follow the instructions above exactly. Makes an extremely noticeable performance difference after running vesa for two months. As an added benefit, the strange horizontal bars on my screen are gone as well!

In fact, all you have to do to switch to using it (assuming your VESA driver is set up properly) is to edit your /etc/X11/xorg.conf (sudo vi /etc/X11/xorg.conf) and replace the vesa line with sis.

It's really a shame that that 3D driver isn't available though, and frankly it doesn't make much sense if it's already written. Most (read: all) resellers of SiS products are not going to be distributing Linux on their machines, so to me it doesn't make much sense to withhold the Linux driver from the community.

---

### Post by pulsifier on 2007-12-11
@Webbie

did you install the driver in feisty then upgrade to gutsy?  this has been driving me mad since gutsy was released, i could never upgrade or install because of the unrecognizable hardware, and feisty only worked after i enabled various boot options, which didnt work for the gutsy live cd.  

btw you have the same exact laptop as i do and i was wondering who the board manufacturer is (im too lazy and swamped with school to check myself) so we could perhaps contact them for the 3D driver.  either that or feebly attempt to put pressure on SiS to make a community release.  anyway, reply here and maybe we could cooperate for some type of joint effort or what have you.

---

### Post by VVebbie on 2007-12-11
I initially did an automatic upgrade, but when that wouldn't boot, I tried a fresh install (using the normal CD). There are two main problems booting the NP7250 with Gutsy, the first is the "progress bar freezes" problem during boot (noapic, nolapic, mentioned on the help file for the CD) and the fact that Gutsy breaks acpi with this laptop (meaning you have no battery indicator). So:

**noapic nolapic acpi=off**

So I upgraded to Gutsy and then installed the driver. Basically I got it working with the correct resolution in VESA, and then just changed to the sis driver in my xorg.conf.

I actually already contacted Sager yesterday about the 3D driver to see if they would try, or would at least give me a lead, but all I got was this slightly amusing reply:

> unfortunately, all our computer are running on Microsoft Windows, we don't
deal with Linux at all.

---

### Post by pulsifier on 2007-12-11
i smell an MS contract. ha.

anyway, thats odd because i tried those boot options with the gutsy live cd.  thanks though, i will give it a whirl with this new driver when time permits.

funny about your email to sager, i emailed them months ago when i first got the computer and they never ever, to this day, replied.  

additionally, if you read the guys blog i originally posted, he said to contact the board manufacturers for the 3D driver, i think MSI makes our boards but i dont know which model.  if you could find out, perhaps we could contact MSI for the 3D driver?  just a thought.

---

### Post by Jerzabek39 on 2007-12-13
> **pulsifier said:**
> i smell an MS contract. ha.

anyway, thats odd because i tried those boot options with the gutsy live cd.  thanks though, i will give it a whirl with this new driver when time permits.

funny about your email to sager, i emailed them months ago when i first got the computer and they never ever, to this day, replied.  

additionally, if you read the guys blog i originally posted, he said to contact the board manufacturers for the 3D driver, i think MSI makes our boards but i dont know which model.  if you could find out, perhaps we could contact MSI for the 3D driver?  just a thought.

Contact MSI is good idea, will you make it?

---

### Post by pulsifier on 2007-12-13
in order to contact MSI i need to know the board model #.  if you can find that out i'll do it.

---

### Post by Jerzabek39 on 2007-12-15
> **pulsifier said:**
> in order to contact MSI i need to know the board model #.  if you can find that out i'll do it.
I´ll try, but now I have no idea where to find it.. :(

---

### Post by Jerzabek39 on 2007-12-31
Any progress here..? :(

---

### Post by pikmaster on 2008-01-11
I downloaded the drivers, copied into /usr/lib/xorg/modules/drivers/ and changed xorg.conf to use sis driver instead of vesa.
But my colors are screwed up.
Did you have the same? I am using Ubuntu Gutsy 7.10

---

### Post by Ropechoborra on 2008-01-13
I also download, copyed and configured Xorg for the Sis drivers, but when i restart X its the same as before.
In the Xorg.conf it says Im using Sis driver, but in System -> Admin -> Screen & Graphics it says that Im still using Vesa driver. And no other resolution than 640x480 or 800x600 is aviable =(

Here is a copy of my Xorg.conf

[http://paste-bin.com/12963](http://paste-bin.com/12963)

Any help will be apreciated.

(Runing ubuntu gusty on my laptop Olibook 520, video Sis 672)

---

### Post by Digger78 on 2008-01-13
> **Ropechoborra said:**
> I also download, copyed and configured Xorg for the Sis drivers, but when i restart X its the same as before.
In the Xorg.conf it says Im using Sis driver, but in System -> Admin -> Screen & Graphics it says that Im still using Vesa driver. And no other resolution than 640x480 or 800x600 is aviable =(

Here is a copy of my Xorg.conf

[http://paste-bin.com/12963](http://paste-bin.com/12963)

Any help will be apreciated.

(Runing ubuntu gusty on my laptop Olibook 520, video Sis 672)

you need to edit the" screen" section of xorg.conf

```
Section "Screen"

        Identifier      "Default Screen"
        Device          "Tarjeta de vídeo genérica"
        Monitor         "Monitor genérico"
        DefaultDepth    24
        [B]SubSection "Display"
		Depth	24
		Modes		"1280x800"	"800x600"	"640x480"
	EndSubSection[/B]
EndSection
```

assuming 1280x800 is the resolution that you want

---

### Post by 0darn on 2008-01-14
how to get info about motherboards ;
-try commands 'sudo dmicode' or 'sudo biosdecode' 
system+bios has to support it+ commands must be in your system 
( if you get a good reply = ok  :) )

heres the info about them; 
[www.nongnu.org/dmidecode](www.nongnu.org/dmidecode)

/ gl 0darn

---

### Post by Jerzabek39 on 2008-01-18
Anybody trying to get this driver from motherboard vendor too..?

---

### Post by Digger78 on 2008-01-18
FSC told me they only had XP & Vista drivers.

I'm currently waiting on a decision from SiS (i aint holding my breath)

I dont understand why they develop drivers if they aint gonna make them available or the mobo manufacturers dont intend making them available.

Its been 7 days since Barros Lee  confirmed that my request for the driver, has been passed on to his supervisor.

I think I will be avoiding SiS chipsets in future

---

### Post by Jerzabek39 on 2008-01-20
> **Digger78 said:**
> FSC told me they only had XP & Vista drivers.

I'm currently waiting on a decision from SiS (i aint holding my breath)

I dont understand why they develop drivers if they aint gonna make them available or the mobo manufacturers dont intend making them available.

Its been 7 days since Barros Lee  confirmed that my request for the driver, has been passed on to his supervisor.

I think I will be avoiding SiS chipsets in future
Great, I´ll looking forward to this answer..

---

### Post by shanka_mns on 2008-01-29
**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+question/23310](https://answers.launchpad.net/ubuntu/+question/23310) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **terrapene said:**
> Well, I contacted this person and told me that a 3D SIS 672 Driver exist, but only can be offered to costumers. As long as SIS is a Chipset manufacturer, its costumers are mainly motherboard builders, not final users. He kindly sends a feisty 2D SIS 672 driver to anyone who asks for it,  I've tried it on my Fujitsu Siemens V5535 and Gutsy and it works fine!!! . Anyway, you can download it from: 
[http://www.badongo.com/file/5319845](http://www.badongo.com/file/5319845)
[http://www.megaupload.com/?d=OO7FNA7X](http://www.megaupload.com/?d=OO7FNA7X)
[http://rapidshare.com/files/72690205/sis_vga_200807_ubuntu_7.04.tgz.html](http://rapidshare.com/files/72690205/sis_vga_200807_ubuntu_7.04.tgz.html)

All you have to do is moving sis_drv.* to /usr/lib/xorg/modules/drivers/ and modify your Xorg.conf from vesa to sis, by typing:

 $sudo dpkg-reconfigure -phigh xserver-xorg .

Well I'm on a 64 bit machine. This driver seems to be only for x86, so it's not working here. Any idea on where I might get the 64 bit version?

I'm on a lenovo 3000H series desktop, details [here]("http://www-604.ibm.com/webapp/wcs/stores/servlet/CategoryDisplay?storeId=10000356&catalogId=-356&langId=356&categoryId=4611686018425111790&productId=4611686018425452141")

It uses a SiS 671 series integrated graphic engine.

---

### Post by Digger78 on 2008-01-29
You could email Barros Lee  -  [email]**barros_lee@sis.com**[/email]

He should either be able to provide a 64 bit driver or provide some more info.

Ask him to pass your e-mail  (requesting 3D driver) to his supervisor.

I still have not had a reply from his supervisor but hopefully if they get enough requests, they will make the driver available on their website.

---

### Post by shanka_mns on 2008-02-03
> **Digger78 said:**
> You could email Barros Lee  -  [email]**barros_lee@sis.com**[/email]
He should either be able to provide a 64 bit driver or provide some more info.


Yeah, I mailed him, he gave me the 64-bit 2D drivers for Mandriva, it works fine with debian. (Anything is better than vesa :) )

Here's the link: [http://rapidshare.com/files/88833100/sis_drv_160707_x86_64_mdv2007.tar.gz.html](http://rapidshare.com/files/88833100/sis_drv_160707_x86_64_mdv2007.tar.gz.html)

move sis_drv.* to /usr/lib/xorg/modules/drivers/
And modify your Xorg.conf from vesa to sis

He also told me:
> It is very sorry that although I am the developer of SiS671 linux 3D driver, I have no rights to send it to you right now. I will keep asking SiS to put all latest drivers on our website.

Hope more mails to him from us, SiS users, actually persuade them to put these on their website.

I bought this computer from Lenovo, I've been asking them to contact SiS about the drivers for the past week without any luck. Anybody else using this approach?

---

### Post by felker2 on 2008-02-08
> **shanka_mns said:**
> Yeah, I mailed him, he gave me the 64-bit 2D drivers for Mandriva, it works fine with debian. (Anything is better than vesa :) )

Here's the link: [http://rapidshare.com/files/88833100/sis_drv_160707_x86_64_mdv2007.tar.gz.html](http://rapidshare.com/files/88833100/sis_drv_160707_x86_64_mdv2007.tar.gz.html)

move sis_drv.* to /usr/lib/xorg/modules/drivers/
And modify your Xorg.conf from vesa to sis

He also told me:


Hope more mails to him from us, SiS users, actually persuade them to put these on their website.

I bought this computer from Lenovo, I've been asking them to contact SiS about the drivers for the past week without any luck. Anybody else using this approach?


Hi, thanks for the 64-bit drivers. I will check if they are as good as the 32-bit drivers.

And yes, I've mailed Maxdata (and Barros Lees himself) to ask SiS for the drivers in a more official way. Maxdata is the supplier/'manufacturer' of my Belinea C 1541 laptop (399 Euro at the MediaMarkt).

---

### Post by punong_bisyonaryo on 2008-02-10
I know this is the 671/672 thread, and my problem is with the 650, but if any one of you can provide some help, check out my problem at [this SiS 650/740 thread]("http://ubuntuforums.org/showthread.php?t=244952&highlight=sis+650")

Thanks!

---

### Post by Jerzabek39 on 2008-02-11
I´ve give a try to Hardy alfa4, does anybody know, how can i reconfigure X server with new Xorg? The reconfigure command doesnt work anymore.. :(

---

### Post by felker2 on 2008-02-12
> **felker2 said:**
> Hi, thanks for the 64-bit drivers. I will check if they are as good as the 32-bit drivers.

And yes, I've mailed Maxdata (and Barros Lees himself) to ask SiS for the drivers in a more official way. Maxdata is the supplier/'manufacturer' of my Belinea C 1541 laptop (399 Euro at the MediaMarkt).

Followup to my own post: I installed the the 64-bit SiS driver onto Ubuntu 7.10 AMD64. After a system reboot (not just a X-server restart!), graphics was great, but the GUI / X-server would halt after a few minutes: a pop-up of Firefox/Gmail trying to include an attachment and a pop-up of Add/Remove Programs would cause a halt. I could still move the mouse pointer, but nothing else worked. Even CTRL - ALT - BackSpace did not stop/restart the X-server. So I had to cold-boot the machine.

The SiS driver on Ubuntu hardy heron 8.04 (with X.org 7.3) is certainly a no-go, both for 32-bit and 64-bit. At least for me; I would like to hear other experiences.

And BTW: still no reply from Barros Lee. :-(

And I thus rediscover: closed source software (like the SiS stuff) is really annoying.

---

### Post by felker2 on 2008-02-13
> **Jerzabek39 said:**
> I´ve give a try to Hardy alfa4, does anybody know, how can i reconfigure X server with new Xorg? The reconfigure command doesnt work anymore.. :(

Jerzabek39, same here: on 8.04 (both 32 and 64 bit) the reconfigure does not work. This could be by design (8.04's X.org 7.3 does need less configuration as it self configures at boot), it could be because the binary SiS driver could only be for X.org 7.2, just a bug or something else.

I've tried to use X.org 7.2's xorg.conf on X.org 7.3, but that didn't work either.

:(

---

### Post by shanka_mns on 2008-02-16
> **felker2 said:**
>  I installed the the 64-bit SiS driver onto Ubuntu 7.10 AMD64. After a system reboot (not just a X-server restart!), graphics was great, but the GUI / X-server would halt after a few minutes

Hey, I also experienced the same problem on my Debian-lenny-amd64, in GNOME, then I tried KDE, seems to work, but opening *any* gnome based application like pidgin or the archive-manager will bring up this problem! Seems like it has to something to with one of the libraries of gtk maybe. But since this is closed source, we'll never know.

---

### Post by vale264 on 2008-02-18
> **shanka_mns said:**
> Hey, I also experienced the same problem on my Debian-lenny-amd64, in GNOME, then I tried KDE, seems to work, but opening *any* gnome based application like pidgin or the archive-manager will bring up this problem! Seems like it has to something to with one of the libraries of gtk maybe. But since this is closed source, we'll never know.

Hi all,
I'm new at this forum. I sent an e-mail to Barros Lee in order to know if there are updated version of the 2D driver that are supported under Ubuntu 7.10, but he answered me that at the moment the 2D driver is not tested under Ubuntu 7.10 64bit. He also sent me the same version of the driver we are playing with.

He replied me that the 3D driver works fine under Ubuntu 7.10 (from his e-mail I understand that this driver supports only the 32bit version of Ubuntu 7.10, but I'm not sure). I'm waiting for his reply to my request where can I download the 3D driver for Gutsy Gibbon...

---

### Post by sokolovss on 2008-02-21
Hi,
I wrote him... he told that he keeps asking SIS for publishing this driver... nothing more...

Why SIS is so slow corporation?:confused:

---

### Post by pulsifier on 2008-02-24
glad to see a number of people are contacting SiS for the 3d driver (and that this thread has been useful).  may i suggest starting a petition to pressure this woeful company into releasing the driver in which we could perhaps threaten a  boycott of SiS products concerning all our future purchases and turning others off to SiS hardware?  just a thought.

---

### Post by sokolovss on 2008-02-24
If you are going to write them, include the link [http://ubuntuforums.org/showthread.php?t=615094](http://ubuntuforums.org/showthread.php?t=615094)

And if they want everybody will write them. Just find their e-mail.

---

### Post by vale264 on 2008-02-25
Hi All,
I'm back with the results of my investigations:

1) I contacted Barros Lee to have some news about the 2D driver for Ubuntu 7.10 64 bit and he sent me the just known 2D driver release that doesn't work under Gutsy Gibbon;
2) I asked Barros Lee where to get the 3D driver and he answered me that he cannot send it outside Sis. The 32 bit 3D driver works properly under Gutsy Gibbon;
3) Barros Lee told me to contact motherboard manifacturer to have the 3D driver, or to contact Sis directly to get it;
4) I sent an e-mail to Sis and an e-mail to Olidata (the Sis chipset integrator for my laptop) in order to get the 3D driver;
5) Sis answered me that they give the code for the generic 3D driver to the 671 chipset integrator in order to make them able to personalize the driver for better performances, and that they don't send the driver to Sis chipset users. They also ask me to contact the motherboard producer to have the drivers;
6) Olidata answered me that they don't have drivers for other operating system than Windows Vista and Windows XP, and they kindly send me the Internet address where to download those Windows drivers... :(

Following the  Barros Lee and Sis suggested steps, there's no way to get the 3D driver. My question is: "Is there a way to get the Linux 3D driver for the 671 Sis chipset?"

I think we have to push Sis company in order to give the Linux community a pubblic version of the 3D driver... What do you think about this approach to the problem?

---

### Post by sokolovss on 2008-02-25
Maybe someone could write this driver himself?

Also I think it's better to ask ubuntu developers.... They can write this driver and include it into Hardy.

Let's find e-mail of ubuntu kernel developers or linux kerneldevelopers and ask them. I wrote this bug to bug.launchpad.net - [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/190960](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-sis/+bug/190960)
[https://bugs.launchpad.net/ubuntu/+bug/194875](https://bugs.launchpad.net/ubuntu/+bug/194875)

So, let's ask ubuntu developers or Linux kernel developers to help us.

---

### Post by pbogu on 2008-02-26
@sokolovss
about your bug report #194875

SIS 661/671 FX - it's not a bug but feature request (missing driver)
SIS 190/191 ethernet driver - it was kernel bug and it is already fixed in 2.6.24
Atheros 5006/5007 EG - driver for this is available by using ndiswrapper, if you don't want to use win drivers then you will have to use madwifi driver. this chipset is supported with madwifi but only on 32b machines, atheros still didn't provide new HAL for 64b. the ticket about that is still open at madwifi's site.

---

### Post by Digger78 on 2008-02-26
I dont think it matters what we do or who we contact, we ain't gonna get the driver.

I just dont understand SiS reluctance to post the downloads on their website, TOTAL MADNESS  if you ask me.

I wouldnt buy a car that could only be driven in reverse, so why should i buy anything with a SiS chipset?...... **from now on i will be completely avoiding anything with a SiS chipset.**


I would hope that the rest of you do the same.

---

### Post by Jerzabek39 on 2008-02-28
> **Digger78 said:**
> I dont think it matters what we do or who we contact, we ain't gonna get the driver.

I just dont understand SiS reluctance to post the downloads on their website, TOTAL MADNESS  if you ask me.

I wouldnt buy a car that could only be driven in reverse, so why should i buy anything with a SiS chipset?...... **from now on i will be completely avoiding anything with a SiS chipset.**


I would hope that the rest of you do the same.

Great idea, but I have my "SiS" laptop now and dont wanna new..:-\"

---

### Post by pulsifier on 2008-02-28
look, i am no computer expert nor am i a linux expert, nor do i profess to be, however, it [I]is[I] apparent that SiS is a worthless company, likewise with Sager.  And when the time comes to purchase a new notebook, it will not have the acronym SiS nor the word Sager within 25 miles of it, plainly put, i fervently hope they lose much business over their apathetic and neglectful attitude towards the linux community.  But the current reality is most of us posting in this thread, myself included, are stranded with our incomplete machines, for at least the next few months.  In light of this might i suggest we download the SiS driver for windows and submit it to Ubuntu developers, the community, or whoever has the knowledge to reverse engineer it so we could finally get the performance we expected when we purchased our machines.  idea or not?

---

### Post by pulsifier on 2008-02-28
the following is a quote from the mandriva site admin regarding the 3D driver:

it sounds like they're willing to make it available on some kind of licensing terms to distributors (like us), but that would only allow allow us to have it in Powerpack release, and given that there's not *really* a lot of SiS users out there, I don't know if we would have the resources to go through all the fun of signing a contract and maintaining the driver as a non-free package :\. I can ask my boss, though.

[http://forum.mandriva.com/viewtopic.php?t=81045&sid=08af353c89cbec38c4539b9b9f5a5083](http://forum.mandriva.com/viewtopic.php?t=81045&sid=08af353c89cbec38c4539b9b9f5a5083)

just thought you might like to know.  apparently SiS is looking to cash in on this.  ridiculous.  well, i'm sorry but it looks like the case is closed.  F-you SiS, i will not purchase your products again in this life time.

---

### Post by sokolovss on 2008-03-01
maybe someone can write this driver? is there any driver programmers?

---

### Post by sokolovss on 2008-03-03
May be something interesting we can find here? [http://www.winischhofer.net/](http://www.winischhofer.net/)

For Example the article: [http://www.winischhofer.eu/linuxsispart4.shtml#download](http://www.winischhofer.eu/linuxsispart4.shtml#download)


Does this driver consist in new Xorg?

---

### Post by uflo2000 on 2008-03-11
mail i get from Barros Lee:

No, My driver is final version. I cannot release 3d driver because I am RD engineer. Actually, SiS don’t want any RD to release any driver. SiS will release driver to customers of SiS (some motherboard vendor).

 

I can release 2d driver, it is due to I ask my boss for this rights, I think this will convenient for end user before SiS release driver on our website. But SiS don’t allowed me to release 3d driver.

 

And about the 2d driver, I don’t know if it work on ubuntu 8.04 or not. We have not try it. All of my colleagues are busy on vista driver recently. But a good news come, my 2d driver colleague told me, we will release driver these days. Maybe this week. 

this is good news. 
So the drivers we all waiting 4 will be hopfully released in a couple of days.

stay tuned ubuntu guys...

---

### Post by Jerzabek39 on 2008-03-11
Thats great news!!!!!!! =D>

---

### Post by vale264 on 2008-03-11
We all cross our fingers!!!

---

### Post by sokolovss on 2008-03-11
We all sell our Notebooks and buy another one :-D

---

### Post by sokolovss on 2008-03-14
I wrote to my motherboard developer

---

### Post by kosmic on 2008-03-15
I Will never ever in my life buy anything that have SiS chipsets inside.

I hope they burn in hell ;)

---

### Post by Xaeryx on 2008-03-17
I downloaded the 2D driver from earlier in the topic but it makes all the colours look messed up, so I had to switch back to VESA.

---

### Post by kosmic on 2008-03-17
In Hardy (Xorg 7.3) the SiS driver don't work, we have to wait for SiS to release the 2D driver ou source of this chip (SiS 671/672) 

:(

---

### Post by sokolovss on 2008-03-17
It will work, but doesn't in Alpha

---

### Post by pulsifier on 2008-03-21
anyone try the 2D driver under 8.04 beta yet?  i just did and can't get resolution above 800x600 with the vsa driver.  SiS 2D does not work.  I'm selling this laptop and buying something running on Intel.

---

### Post by Jerzabek39 on 2008-03-22
> **pulsifier said:**
> anyone try the 2D driver under 8.04 beta yet?  i just did and can't get resolution above 800x600 with the vsa driver.  SiS 2D does not work.  I'm selling this laptop and buying something running on Intel.

I wrote it before, same problem. :mad:

---

### Post by pulsifier on 2008-03-25
i hate SiS.  looks like i learned this lesson the hard way.

---

### Post by zorglups on 2008-03-28
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?p=4558160](http://ubuntuforums.org/showthread.php?p=4558160) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **pulsifier said:**
> anyone try the 2D driver under 8.04 beta yet?  i just did and can't get resolution above 800x600 with the vsa driver.  SiS 2D does not work.  I'm selling this laptop and buying something running on Intel.

I tried it as well but could not get the Intel driver to work on 8.04 beta.
It falls back to vesa which won't suit my mythtv setup.

I just found this thread but I'm too bad in compiling without a good how-to:
[http://ubuntuforums.org/showthread.php?p=4558160]("http://ubuntuforums.org/showthread.php?p=4558160")

Just in case someone want to give it a try.

Best regards,

Pierre.

Note: I hate SiS too now but still can't see any fanless MB that could compete with this baby. I will keep trying.

---

### Post by PlOkIjUh on 2008-04-01
> **zorglups said:**
> 

I tried it as well but could not get the Intel driver to work on 8.04 beta.
It falls back to vesa which won't suit my mythtv setup.

I just found this thread but I'm too bad in compiling without a good how-to:
[http://ubuntuforums.org/showthread.php?p=4558160]("http://ubuntuforums.org/showthread.php?p=4558160")

Just in case someone want to give it a try.


Gave it a try - wasn't super easy, but no it doesn't work. It's just a patched version of the normal old sis driver.

Has anyone managed to get hold of a compiled 2D driver for Xorg 1.4.0 that comes with Hardy?

---

### Post by Libertino on 2008-04-06
Hey all, I also bought an esprimo Mobile 5335 from Fujitsu Siemens  and I am having problems with the SiS Mirage 3 Graphics driver. I tried to apply the driver from rapidshare as recommended above in gutsy and modified my xorg.conf. However, I still only get vesa resolution and cannot put the resolution to 1280x800,  although 1280x800 is in the xorg.conf and Sis-Driver is in Administration/system/Screen & graphics.

what do I do wrong? who can help?
Is there a better driver available from SiS now? I would even be happy with a 2D only one.

I am not sure, that the SiS chip is a 671/672. Neither is offered in the Administration/systems/Sreen&Graphics dialogue. Choosing 650 didn't make anything better.

Libertino

---

### Post by Digger78 on 2008-04-07
> **Libertino said:**
> Hey all, I also bought an esprimo Mobile 5335 from Fujitsu Siemens  and I am having problems with the SiS Mirage 3 Graphics driver. I tried to apply the driver from rapidshare as recommended above in gutsy and modified my xorg.conf. However, I still only get vesa resolution and cannot put the resolution to 1280x800,  although 1280x800 is in the xorg.conf and Sis-Driver is in Administration/system/Screen & graphics.

what do I do wrong? who can help?
Is there a better driver available from SiS now? I would even be happy with a 2D only one.

I am not sure, that the SiS chip is a 671/672. Neither is offered in the Administration/systems/Sreen&Graphics dialogue. Choosing 650 didn't make anything better.

Libertino

You will need to edit your xorg.conf  - adding the bold text to the appropriate section

```
Section "Monitor"
   Identifier   "Generic Monitor"
   Option      "DPMS"
   [B]HorizSync 28-72
   VertRefresh 43-60[/B]
EndSection

```

then restart X

---

### Post by ottod on 2008-04-11
See [here]("http://ubuntuforums.org/showpost.php?p=4697207&postcount=4") for some help.

---

### Post by Jerzabek39 on 2008-04-14
Any news...? :confused:

---

### Post by LordSavage on 2008-04-14
I need the driver too!

---

### Post by LordSavage on 2008-04-15
2D driver is enought but please, I need the driver for hardy!

---

### Post by pulsifier on 2008-04-17
so does everyone else in this thread since it started 5 months ago.  it SiS's fault, they refuse to develop for linux.  i know where my tax refund is going.  to a new laptop with Intel inside and ill trash this SiS junk.

---

### Post by pjasnos on 2008-04-18
Hi,

It looks like SiS (or at least one of their employees) is actually trying to support 671 on Linux - look at the commit history to the latest kernel revision.

[http://kerneltrap.org/mailarchive/git-commits-head/2008/2/20/917674](http://kerneltrap.org/mailarchive/git-commits-head/2008/2/20/917674)

Mayby we should try to contact Chaoyu Chen instead of Barros Lee?
I would have done that if my English was better... :wink:

---

### Post by pjasnos on 2008-04-22
I found a source code for the 2D driver :) (and I think that's the one that Barros Lee is sending, as some files have SiS copyright:) ), so that any of you guys using Hardy or x64 can compile that :). It needs a newest kernel, or a patch, if you want to stick with the older version, in order to enable detection of the chipset.

a driver (and a kernel patch) is here:
[http://www.linuxconsulting.ro/xorg-drivers/](http://www.linuxconsulting.ro/xorg-drivers/)

and, in case you need, a nice tutorial on kernel compiling:
(should work for any version, but I'd rather use sudo instead of changing root password ;)

[http://howtoforge.com/kernel_compilation_ubuntu](http://howtoforge.com/kernel_compilation_ubuntu)

:popcorn:

---

### Post by Jerzabek39 on 2008-04-23
> **pjasnos said:**
> I found a source code for the 2D driver :) (and I think that's the one that Barros Lee is sending, as some files have SiS copyright:) ), so that any of you guys using Hardy or x64 can compile that :). It needs a newest kernel, or a patch, if you want to stick with the older version, in order to enable detection of the chipset.

a driver (and a kernel patch) is here:
[http://www.linuxconsulting.ro/xorg-drivers/](http://www.linuxconsulting.ro/xorg-drivers/)

and, in case you need, a nice tutorial on kernel compiling:
(should work for any version, but I'd rather use sudo instead of changing root password ;)

[http://howtoforge.com/kernel_compilation_ubuntu](http://howtoforge.com/kernel_compilation_ubuntu)

:popcorn:

So its possible to have 2D driver on 8.04?

---

### Post by pjasnos on 2008-04-24
notes on the page whose address I provided seem to indicate, that the driver should work with any X.org version >= 7.0, so I think it should (but I haven't tried as I am using Gutsy because of my wifi card driver not working properly on kernels newer that 2.6.22).

Which version of kernel does 8.04 have? if lower than 2.6.24, you will need to install (or compile yourself) a newer kernel.

uname -a should show kernel version :)

N.B. I may have a go at compiling it in Hardy on weekend (and then writing a tutorial :) ), but only if I manage to complete my student loan application.

---

### Post by Jerzabek39 on 2008-04-25
Somebody using our graphic card on 8.04..?

---

### Post by pjasnos on 2008-04-25
Me :) :)!! 

Just compiling what I found on other thread and on the net and will be posting it shortly :).

---

### Post by pjasnos on 2008-04-25
"almost" point and click method:

Get OttoD modified sources (n.b. he posted a link on this thread, but just in case:

[http://ubuntuforums.org/showpost.php?p=4697207&postcount=4](http://ubuntuforums.org/showpost.php?p=4697207&postcount=4)

```
sudo apt-get build-dep xserver-xorg-video-sis

sudo apt-get install displayconfig-gtk

tar -xjf intelsrc.tar.bz2

cd 2d-driver

./configure --prefix=/usr

sudo make install

sudo displayconfig-gtk
```

Click on Graphics Card --> Driver --> Choose driver by name --> sis (Silicon Integrated Systems)

Go back to Screen, click Model and select appropriate resolution from generic (in my case:
 Generic LCD Panel 1280x800), remember to tick widescreen box if your monitor is widescreen

Choose appropriate screen resolution

Done :)


N.b. if you run displayconfig-gtk again, it will say that you are using Vesa, and so will xorg.conf, but that's not true, as X autoconfigures itself to use sis. (displayconfig-gtk is somewhat deprecated in Hardy AFAIK --> see 
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/207409](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/207409)
because of X.org 7.3)

---

### Post by pjasnos on 2008-04-26
Now just need to wait for the 3D driver....

---

### Post by Jerzabek39 on 2008-04-26
> **pjasnos said:**
> Me :) :)!! 

Just compiling what I found on other thread and on the net and will be posting it shortly :).

Great, thank you!!! :)

---

### Post by andreabu on 2008-04-28
Worked for me too ! Had to work around that screen resolution utility a bit but seems fine now, 1024x768 on LCD OK... Thank you all !!

---

### Post by robinPain on 2008-05-01
Thank you Pjasnos!

At long last it works!

(It compiled the sis_drv* in another path so I had to do this also):

sudo mv /lib/xorg/modules/drivers/sis_drv* /usr/lib/xorg/modules/drivers/

--Oh no, spoke too soon, it reverts to low res after power down/up :(

Rob

---

### Post by pjasnos on 2008-05-01
> **robinPain said:**
> Thank you Pjasnos!

At long last it works!

(It compiled the sis_drv* in another path so I had to do this also):

sudo mv /lib/xorg/modules/drivers/sis_drv* /usr/lib/xorg/modules/drivers/

--Oh no, spoke too soon, it reverts to low res after power down/up :(

Rob

hmmm... you may try editing /etc/X11/xorg.conf

in terminal: gksudo gedit /etc/X11/xorg.conf

find the part with Driver "vesa" and change it to Driver "sis"

---

### Post by DrGang06 on 2008-05-02
Just for infomation, OttoD modified sources can work on mandriva 2008.1 with some changes ... you have to install several pakages and delete #include xf86_ansic.h in /src/sis.h !
That's all :)
Tom

---

### Post by dirkvic on 2008-05-03
pjasnos' recipie worked fine on my Fujitsu siemens v5535, but before it worked I had to manually enter SiS into /etc/X11/xorg.conf .

sudo gedit /etc/X11/xorg.conf

...
Section "Device"
	Identifier	"**sis**"
EndSection
...

Then restarted and;

sudo displayconfig-gtk

Selected "LCD Panel 1024x768".

Restart and all OK. Thankyou all.

---

### Post by dummiebeginner on 2008-05-03
Hi, I a total beginner. I have this Fujitsu-Siemens Esprimo Mobile V5355 and I am desperately trying to make the SIS672 driver to work for linux as I need to learn to use it but won't display more than 800x600 without that driver as you all know well.

I have been searching for days, exahusted, and found this thread were you seem to have found a way to make it work.

Now, the problem is that those instructions are chinese to me. I know little about computers, just a veteran user of Windows where I feel comfortable, but NOTHING about Linux coding, those code strings you talk about, in order to change things...

I know this must be terribly boring, but without learning it I will never be able to use Linux in my computer. So, is someone so kind to explain me step by step what I have to do to install that bl**dy driver?

Thanks a lot in advance.

---

### Post by Poszumtak on 2008-05-04
Dummiebeginner, first, download "intelbin.tar.bz2" from here:
[http://ubuntuforums.org/showpost.php?p=4697207&postcount=4](http://ubuntuforums.org/showpost.php?p=4697207&postcount=4)
Unpack it (by right clicking on it -> Extract here). 
Then go to menu Applications->Accesories->Terminal. It is where you can type commands (for example these listed in posts above). I don't know if you already knew that, but I said this just in case ;)
Now you must go to that extraxted folder you've just downloaded. You can make this in terminal using command "cd":
```
cd intelbin
```
or:
```
cd Desktop/intelbin
```
if you have downloaded this to your Desktop.
First of all we will make backup of graphic configuration file called xorg.conf which is in /etc/X11 folder by typing command "cp":
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
Now just copy files and folders in intelbin folder by command "cp -R" (you must use command "sudo" which will copy that files with administrator previliges (in Linux administrator is called "root"):
```
sudo cp -R * /
```
"/" is your main system folder where we just copied all files and folders (by typing "*") from folder intelbin.
Now restart your computer (or you can just logout and login). By default this will set your keyboard layout to Spanish. You can change it in menu System->Preferences->Keyboard (second tab). In my case that was all ;)
That method have one disadvantage - it made that my touchpad in laptop doesn't have any special features like scrolling.
I hope this is anderstandable because of my not so good english ;)

---

### Post by d-zug on 2008-05-04
Thanks for the excellent description. You should give it to the Ubuntu-Developers to implement the driver in the following Releases.

---

### Post by dummiebeginner on 2008-05-04
Thanks a lot Posztumak, you are very kind. I will try to do it and see what happens. 

I am finding some previous problems:

- In order to install the driver, I must install Ubuntu first, right? I mean not just the live CD but the WHOLE installation. Am I wrong?

- Then I face two problems: First, when I try to install it, because the screen resolution is just 800x600, it gets to a window where it asks for your  country, and funny enough, the window is so big that the bottom buttons to go forward are hiddenand you can't move the window up. It's crazy but true! You can't do anything to see them. Given that I am very persistant, I found out that by pressing ENTER it worked, but at some points of the installation you go kind of blind and don't know what you are pressing. If you knew of another alternative to going blind for moving the window up please let me know.

- Second, when it comes to the installation and disk partition, it's crazy for a beginner. Just impossible to know what you must choose and other questions it asks. I read a lot on that but still... you must go sort of blind.

In this very moment I am writing from another computer and installing Ubuntu in the laptop. Let's see what happens, I'll keep you informed but in any case THANKS A LOT. This explanations for beginners should be kept and published for everyone with this laptops and graphic cards.

---

### Post by Poszumtak on 2008-05-04
As far as I know - yes, you can install this driver using LiveCD, but you must logout, login (if you restart comuter you will lose your settings) to changes take effect.

---

### Post by dummiebeginner on 2008-05-04
Ok, it didn't work.

When I restart it seems to start all over again. The intelbin file and folder that I place in the desktop disappears from one session to the other, and the CD takes ages to load as starting from zero.

So, I don't know if that is the reason or not but doesn't work.

This is exactly what I did_

- Download intelbin[1].tar.bz2 and ignore the other one from that post of Otto
- Place intelbin[1] in desktop and unzip it right there
- Rename intelbin[1].tar.bz2 for intelbin (remove the number 1)

- Then type exactly:

cd Desktop/intelbin (ENTER)

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup (ENTER)

sudo cp -R * /

Did I do anything wrong? (this is a nightmare, really, Linux is too difficult). Apart from that, Firefox doesn't load anything in this Ubuntu. It loads well Google but nothing else, so I need to close Ubuntu all the time just to use internetand load it again all the time, takes hours and hours and hours just for something which should be very quick and easy like this try-out system for beginners.

Thanks!

---

### Post by Poszumtak on 2008-05-04
> **dummiebeginner said:**
> When I restart it seems to start all over again.
I mentioned that in previous post - if you are on LiveCD (without installed Ubuntu) you should Logout (and then Login again), not to restart computer ;)

---

### Post by dummiebeginner on 2008-05-04
Yes, my bad. It works when logging off and on, I made that mistake. Excellent, thanks a lot!

Now, I can't navigate... Firefox only loads Google. It works with the searches showing results but doesn't open the links... so I tried to install another program called Epiphany using this Pack Manager but the download fails all the time. I thought that this system was better and more solid but seems to be a nerves destroyer.

Thanks again!

---

### Post by dummiebeginner on 2008-05-05
Too good to be true... problems again.

It worked perfectly, and then I installed the whole program from the 1200x800 resolution, but when it restarted, it was gone and returned to 800x600. So, now I have the program installed and running well but when I tried to repeat the driver installation in the Terminal it asked me for my administrator password (which I inserted) but later will say that CD DESKTOP/INTELBIN doesnt exist...

Any suggestion? Ubuntu works well but in 800x600 again. 

THANKS!

---

### Post by dirkvic on 2008-05-05
You should copy the driver files (sis_drv.la, sis_drv.so) into the folder /lib/xorg/drivers/ .

Then edit /etc/X11/xorg.conf in the following section;

```

Section "Device"
	Identifier	"sis"
EndSection

```

Then run sudo displayconfig-gtk

This is only from earlier walk-throughs which worked for my V5535 fujitsu siemens. Someone might want to verify that it is correct.

---

### Post by Digger78 on 2008-05-05
> **dummiebeginner said:**
> Too good to be true... problems again.

It worked perfectly, and then I installed the whole program from the 1200x800 resolution, but when it restarted, it was gone and returned to 800x600. So, now I have the program installed and running well but when I tried to repeat the driver installation in the Terminal it asked me for my administrator password (which I inserted) but later will say that CD DESKTOP/INTELBIN doesnt exist...

Any suggestion? Ubuntu works well but in 800x600 again. 

THANKS!

I assume you have now installed ubuntu? the file(s) you downloaded using the live CD will no longer exist as they were held in RAM, (nothing was written to disk) simply download them again.

---

### Post by Digger78 on 2008-05-05
> **dirkvic said:**
> You should copy the driver files (sis_drv.la, sis_drv.so) into the folder /lib/xorg/drivers/ .

Then edit /etc/X11/xorg.conf in the following section;

```

Section "Device"
	Identifier	"sis"
EndSection

```

Then run sudo displayconfig-gtk

This is only from earlier walk-throughs which worked for my V5535 fujitsu siemens. Someone might want to verify that it is correct.


I havent upgraded to Hardy yet, so i am not sure how displayconfig-gtk works but i would be tempted to add the driver line.

```

Section "Device"
	Identifier	"sis"
        **Driver          "sis"**
EndSection

```

---

### Post by debianite on 2008-05-06
Hi, I have been following this topic almost since the beginning, as i own a Fujitsu Siemens mobile with the infamous SiS 672 igp.
Although i don't have Ubuntu installed (i use Debian Lenny), i'm plagued with the same problem as every body else, for now I'm stuck with this hardware but rest assured that never again i will buy anything from sis.
The 2D driver provided by Mr. Lee Barros worked well before the last update of xorg packages in Debian Testing, after that they no longer worked, then i tried to compile the source drivers provides by pjasnos to no avail. 
when i cp the binaries together with mi saved xorg.conf it all stared to work as before, it was very important to replace the xorg.com with the old one as ```
dpkg-reconfigure xserver-xorg
``` doesn't work has it used to.

---

### Post by scarecrowmeat on 2008-05-09
I followed the steps for installing the driver but when it got to the configuration dialog (sudo displayconfig-gtk) i can select SIS and my resolution etc, but when i click test, the display crashes (Green lines coming from the top of the screen) and then i get a message telling me that "Configuration test failed". And if i apply the settings things don't change. 

Anyone have any idea why this is happening?

I am running Hardy Heron on an Advent 9415 with what i only before looking into this knew as "SIS mirage 3 graphics" as an igp graphics card. I'm assuming this is what the SIS 671/672 cards are?

Any help greatly appreciated. :(

If only SIS would just provide the drivers :mad:

---

### Post by debianite on 2008-05-10
> If only SIS would just provide the drivers 

We all have to to keep emailing them and request the drivers, including the link to this tread may also help.

---

### Post by jpescolar on 2008-05-11
> **pjasnos said:**
> "almost" point and click method:

Get OttoD modified sources (n.b. he posted a link on this thread, but just in case:

[http://ubuntuforums.org/showpost.php?p=4697207&postcount=4](http://ubuntuforums.org/showpost.php?p=4697207&postcount=4)

sudo apt-get build-dep xserver-xorg-video-sis

sudo apt-get install displayconfig-gtk

tar -xjf intelsrc.tar.bz2

cd 2d-driver

./configure --prefix=/

sudo make install

sudo displayconfig-gtk

Click on Graphics Card --> Driver --> Choose driver by name --> sis (Silicon Integrated Systems)

Go back to Screen, click Model and select appropriate resolution from generic (in my case:
 Generic LCD Panel 1280x800), remember to tick widescreen box if your monitor is widescreen

Choose appropriate screen resolution

Done :)


N.b. if you run displayconfig-gtk again, it will say that you are using Vesa, and so will xorg.conf, but that's not true, as X autoconfigures itself to use sis. (displayconfig-gtk is somewhat deprecated in Hardy AFAIK --> see 
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/207409](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/207409)
because of X.org 7.3)
In my 64 bits hardy laptop I've to copy the files installed in the lib64 dir to the correct dir:  

cp /lib64/xorg/modules/drivers/sis_drv.so /usr/lib64/xorg/modules/drivers/sis_drv.so

And work very fine.

Thanks a lot!

---

### Post by Pablin on 2008-05-12
I must say Thank you very much pjasnos!!!!!! your driver works correctly in my Olibook 520 with the "SiS 671/672 Mirage 3 Graphics" Graphic Card running Kubuntu 8.04 Hardy Heron.

Again thank you very much pjasnos and sorry for my poor english.

---

### Post by dummiebeginner on 2008-05-12
Hi again,

I regret to say that it finally didn't work for me, Poszumtak. For some reason I couldn't access the forum that day anymore and couldn't reply to you when I was trying to solve this and I got too tired and stressed so I sent everything to hell and reinstalled Windows (apart frpm the fact that Ubuntu self-installed over my whole hard disk formatting my Windows and I got like arrrghhh!!)

Ok, the question is still the same. It works well from the CD and I get 1200x800. But then I install Ubuntu from the desktop install icon and when it's done, the resolution returns to 800x600, and when I try to log off and on as you nsuggest, it asks me for an administrator password to log in, which I insert, and later when I try to write the code (for installing the driver again) in the console CD DESKTOP/INTELBIN, something has been modified (because of the administrator log-in probably) and it says that such directory or file don't exist while I still see the bl**dy driver folder over my desktop.

So, some instruction is missing at that point. If you know what I'm talking about, please let me know what I'm doing wrong.

Thanks again

PS: Yes, I use version 8.04. Should I try version 7.10 with another system? Anyone knows of this possibility and can explain in words for dummies?

Thanks

PS2: I forgot to say that this notebook uses 64bits, I believe. Does it matter what Ubuntu I'm using, 32 or 64? Because I don't remember which one I got... My Windows is 32 bits and I perhaps got the 32 for Ubuntu as well to avoid problems since 32 runs in 64 and not the other way round I believe.

---

### Post by pjasnos on 2008-05-12
> **jpescolar said:**
> In my 64 bits hardy laptop I've to copy the files installed in the lib64 dir to the correct dir:  

cp /lib64/xorg/modules/drivers/sis_drv.so /usr/lib64/xorg/modules/drivers/sis_drv.so

And work very fine.

Thanks a lot!

Hello,

Just a few words: this is not my driver, it was released by Intel and modified by OttoD to make it work with Xorg 7.3 (which is default in Hardy) --> and I want to say a BIG thank you to him for that. 

jpescolar: I installed the files in /lib/xorg/modules and didn't have problems making it work. If you want them to go to /usr/lib64/xorg/modules (or /usr/lib/xorg/modules), please use

[B]./configure --prefix=/usr
[/B]
instead of:

./configure --prefix=/

---

### Post by subcomandante on 2008-05-13
Que grande pjasnos, todo perfecto siguiento paso a paso las indicaciones de la pagina 8, en kubuntu 8.04 en una olibook

Gracias

thanks pjasnos your driver works fine in Kubuntu 8.04.

---

### Post by scarecrowmeat on 2008-05-13
> **pjasnos said:**
> Hello,

Just a few words: this is not my driver, it was released by Intel and modified by OttoD to make it work with Xorg 7.3 (which is default in Hardy) --> and I want to say a BIG thank you to him for that. 

jpescolar: I installed the files in /lib/xorg/modules and didn't have problems making it work. If you want them to go to /usr/lib64/xorg/modules (or /usr/lib/xorg/modules), please use

[B]./configure --prefix=/usr
[/B]
instead of:

./configure --prefix=/
\\:D/
Thanks! for me it was installing the files to the directories under /usr that fixed it (I'm running Ubuntu Hardy).

---

### Post by lucano22 on 2008-05-14
> **pjasnos said:**
> "almost" point and click method:

Get OttoD modified sources (n.b. he posted a link on this thread, but just in case:

[http://ubuntuforums.org/showpost.php?p=4697207&postcount=4](http://ubuntuforums.org/showpost.php?p=4697207&postcount=4)

```
sudo apt-get build-dep xserver-xorg-video-sis

sudo apt-get install displayconfig-gtk

tar -xjf intelsrc.tar.bz2

cd 2d-driver

./configure --prefix=/usr

sudo make install

sudo displayconfig-gtk
```

Click on Graphics Card --> Driver --> Choose driver by name --> sis (Silicon Integrated Systems)

Go back to Screen, click Model and select appropriate resolution from generic (in my case:
 Generic LCD Panel 1280x800), remember to tick widescreen box if your monitor is widescreen

Choose appropriate screen resolution

Done :)


N.b. if you run displayconfig-gtk again, it will say that you are using Vesa, and so will xorg.conf, but that's not true, as X autoconfigures itself to use sis. (displayconfig-gtk is somewhat deprecated in Hardy AFAIK --> see 
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/207409](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/207409)
because of X.org 7.3)
Hey man that worked ok!... thanks a lot!.... but I'm still fighting with the fu##### wifi... you know... at startup with pci=aasign-busses apic miantimer idle=poll reboot=cold, hard I can enable the Wifi but I can see the accsess point but can't connect to. With noapic nolapic acpi=off irqpoll I can't enable the wifi card.........

Someone has solve this issue?????

Thanks and regards,

---

### Post by pjasnos on 2008-05-14
lucano: you didn't say the most important thing (IMHO) - the model/make of your wifi card... Also, I think this should go to a new topic.

---

### Post by ahaertig on 2008-05-15
Hallo pjasnos,

could you please post your compiled drivers?
This would be very helpfull for people not familiar with compiling software.

---

### Post by pjasnos on 2008-05-15
> **ahaertig said:**
> Hallo pjasnos,

could you please post your compiled drivers?
This would be very helpfull for people not familiar with compiling software.

You can find binary version here:
[http://ubuntuforums.org/showpost.php?p=4697207&postcount=4](http://ubuntuforums.org/showpost.php?p=4697207&postcount=4)

I feel that I have provided detailed & exhaustive instructions on how to compile the drivers, if you've got any problem with them please ask (and if you don't want to learn you shouldn't be here). 

Linux is open source and IMHO one should use binary packages only if compilation takes very long time (I've attempted to compile KDE on my old computer, but gave up after 30 hours) - these drivers compile in less than a minute on my machine.

---

### Post by AquilaM on 2008-05-17
Finally. I've been looking for a solution for this SIS graphics problem for a long time. Pjasnos, it is my humble opinion that you deserve a beer or two after work today. Thanks a lot my friend.

Ehhh...if you're under 18, then maybe you have to settle for a glass of milk.

---

### Post by olbion on 2008-05-19
Hi all,

I've read this discussion with interest as I am another owner of a Fujitsu V5535. I've managed to install Ubuntu 8.04 with the sis drivers provided here - thank you very much for that. I still have two problems though:

1. Video playback in fullscreen seems to be impossible, in any video player (VLC, Mplayer etc). Is this a video driver issue? Or is there perhaps some simple solution?

2. I can't set a separate resolution when using an external monitor. Ideally, I'd like to use 1280x1024 instead of 1280x800. Does anyone know if this is possible, and if so, how?

---

### Post by colinnwn on 2008-05-19
Hi,

I tried following pjasnos's directions exactly.  It looked like everything worked until I got to the last line

```

colin@myth-1:~/Desktop/2d-driver$ sudo displayconfig-gtk
/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:72: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
Traceback (most recent call last):
  File "/usr/bin/displayconfig-gtk", line 75, in <module>
    app = DisplayConfig(options)
  File "/usr/lib/python2.5/site-packages/displayconfiggtk/DisplayConfig.py", line 71, in __init__
    gtk.init_check()
RuntimeError: could not open display

```

I'm doing this on Mythbuntu 8.04 running XFCE.  I wasn't sure where the analogue to Graphics Card --> Driver --> Choose driver by name --> sis (Silicon Integrated Systems) is.  I looked at Applications>System>Hardware Drivers, but it says 'No proprietary drivers in use on this system'

Can anyone help me get past this?
Thanks.

---

### Post by colinnwn on 2008-05-20
I was going strictly by the directions, but decided what the hey, restarted, and sudo displayconfig-gtk.  Everything worked fine from there.  Maybe it was because I initially used SSH and this time I used the terminal on the desktop?  The SiS video card is working a thousand percent better. [B]Thanks pjasnos! 
[/B]
I think I have one last question for this thread.  I recorded some over the air digital TV shows, so they are pure MPEG-2 streams never transcoded when I was using the VESA display driver.  They would play, but the screen would only update once every several seconds.  Now when I play them with the SiS driver in full screen mode all I see is horizontal stripes.  But when they automatically preview in the 'select recordings to watch' screen, they play completely normal.  

Does anyone have any idea if switching from the VESA to the SiS driver could have actually caused this?  Does anyone have an idea on how I could watch these in full screen mode?

Thanks All.

---

### Post by rekado on 2008-05-26
I've got a new Haier A20 notebook with Intel Dual Core T2370 and the infamous SiS M671 Mirage 3 "running" Ubuntu 8.04 in the 64 bit version. I had to install Ubuntu with the options "noapic nolapic acpi=off vga=791"; now I boot it with the options "noapic acpi=off".

I followed all instructions in this thread and various others, also contacted Chen Chao Yu from SiS and got the latest original source (2D only) as of November 2007.

Now it does kind of work, I get the full screen resolution at 1280x800px but some things are still very very odd:


[LIST=1]
[*]when booting up or testing the driver+screen setup with displayconfig-gtk the screen looks really scary: in the left lower corner there is an almost solid turquoise rectangle (about 2cm wide and with different heights on each occasion) while the rest of the screen has a pale turquoise-grayish raster which looks similar to a radial gradient, edges fading to black. This raster will be visible for about a second or two while the brightness of the pattern increases steadily (first time I saw it I thought my LCD will break...).

[*]Whenever I manually change /etc/X11/xorg.conf and restart X or reboot the resolution is back at 800x600 @ 61Hz again (why 61 and not 60?). Then I have to setup the resolution and the driver with displayconf-gtk again, which does not always work (sometimes the maximum resolution shown is 1280x786 or the driver cannot be changed or the test fails completely)

[*]My xorg.conf is extremely short, not even listing any resolution settings at all! Also my Synaptics trackpad is not listed; adding it will reset the resolution to 800x600 at next boot...

[*]Videos in Totem or VLC don't play at fullscreen. Double-clicking on the window or scaling it will not change the video size.

[*]Another weird thing (probably related to ACPI): whenever I run displayconfig-gtk or dpkg-reconfigure -phigh xserver-xorg I get the following error two times:
```
FATAL: Error inserting battery (/lib/modules/2.6.24-16-generic/kernel/drivers/acpi/battery.ko): No such device
```
dpkg-reconfigure -phigh xserver-xorg then aborts while displayconfig-gtk would continue loading. This error also occurs during booting up in verbose mode.
[/LIST]

Does anyone experience something similar?
Weird enough the Fn-keys all do work (which is a problem on my other Haier notebook [A61])...

I would be happy if someone could tell me if that all is just normal or if there is a workaround.

Thanks,

Rekado

---

### Post by ahaertig on 2008-05-27
It seems like SIS updated their drivers for Hardy.
Go on and catch it: [http://barroslee.blogspot.com/2008/05/sis-linux-2d-driver-for-ubuntu-804.html]("http://barroslee.blogspot.com/2008/05/sis-linux-2d-driver-for-ubuntu-804.html")

---

### Post by debianite on 2008-05-27
Can any one post a link to the updated drivers?
Thanks.

---

### Post by mihailojocic on 2008-05-27
Here is link to new SiS 671 ubuntu 8.04 driver and short letter from Barros Lee

;-)

[http://rapidshare.com/files/118140763/sis_vga_150508_ubuntu_8.04.tar.bz2.html](http://rapidshare.com/files/118140763/sis_vga_150508_ubuntu_8.04.tar.bz2.html)

Dear all,

Here is our 2d driver for Ubuntu 8.04, you can try it first.
Please move sis_drv.* to /usr/lib/xorg/modules/drivers/
And modify your Xorg.conf
Add Driver "sis" in Section "Device"

Best Regards
Barros Lee

Thanks to Barros Lee and Denner Peterlini who send me this driver

---

### Post by rekado on 2008-05-28
Barros Lee contacted me directly and send me the binaries of the new driver for Ubuntu 8.04 (32bit). I also asked him for the source code, hope he can send it to me soon.

Chen Chao Yu also replied to my mail but could only provide the already known driver source code which he maintained until November 2007. He told me that SiS signed contracts with other companies which prevents him to publish the OpenGL driver privately; as I understand, though, the driver exists and is distributed to manufacturers. I will contact Haier China soon in order to inquire the 3D driver.

Attached you can find both the binaries Barros Lee send to me and the source code Chen Chao Yu provided.

To use the driver binaries please move sis_drv.* to /usr/lib/xorg/modules/drivers/
and modify your Xorg.conf by adding 'Driver "sis"' in section "Device".

Hope that helps!


EDIT: sorry, the binaries are too big to attach (just some 50kB bigger than the limit) - i could email them to you, though.
EDIT: weird, the previous upload obviously failed... once again (so embarrassing)
EDIT: added the binaries as 7z (hope it works this time) - remove the ".svg"-part; I just added it to be able to upload the file...

---

### Post by kajaman13 on 2008-05-29
Hi guys,

I'm another unfortunate esprimo owner. I installed the binary driver from ottod and the resolution is what it should be. Big thanks to everybody involved. 
The video in xine is running fast enough, BUT IT WOULD'T RESIZE. 
Seems to be a driver problem to me. Anybody has the same experience? Any suggestions?

---

### Post by rekado on 2008-05-29
Yeah, this has been reported in this thread two times before; so now we are three. I don't know of a workaround.

---

### Post by ifp5 on 2008-05-29
Could anybody e-mail me a source or binary for 8.04 64-bit? ivan.panachev <at> gmail.com

---

### Post by Sprogg2001 on 2008-05-29
> **mihailojocic said:**
> Here is link to new SiS 671 ubuntu 8.04 driver and short letter from Barros Lee

;-)

[http://rapidshare.com/files/118140763/sis_vga_150508_ubuntu_8.04.tar.bz2.html](http://rapidshare.com/files/118140763/sis_vga_150508_ubuntu_8.04.tar.bz2.html)

Dear all,

Here is our 2d driver for Ubuntu 8.04, you can try it first.
Please move sis_drv.* to /usr/lib/xorg/modules/drivers/
And modify your Xorg.conf
Add Driver "sis" in Section "Device"

Best Regards
Barros Lee

Thanks to Barros Lee and Denner Peterlini who send me this driver


Thank you for that mihailojocic can anyone confirm if they still have resizing issues with the above driver (I´m a victim of this as well) is it the same driver as the OttoD modified intel source 

Which one should I be using 

thanks in advance

---

### Post by dummiebeginner on 2008-05-29
My Windows crashed again after another virus and I had to format and reinstall once again. I am desperate.

I tried the different methods you describe here to instll this bl**dy driver in my Esprimo but I just don't know how Linux works and those instructions are chinese to me.

Could somebody please be so kind to explain step by step how to do this? For instance I tried to copy (move) the drivers from the desktop to the drivers folder but it sais it was impossible as I needed administrator privileges. I mean, it's just chinese for any beginner. I've tried a million times and read every manual but still you say things that I don't understand at all (compiling for instance...?¿?¿ what is that?)

Anyone please? Easy step by step instructions as you'd tell your grandmother if she needed them for surviving?

---

### Post by mihailojocic on 2008-05-30
> **Sprogg2001 said:**
> Thank you for that mihailojocic can anyone confirm if they still have resizing issues with the above driver (I´m a victim of this as well) is it the same driver as the OttoD modified intel source 

Which one should I be using 

thanks in advance


I don't have resizing issues and if you ask me you should copy those files from link above. I was try OttoD driver and I wasn't happy. I think that isn't the same driver. If you use ubuntu 8.04 driver from barros lee is option number one.

thanks for thanks :)

---

### Post by mihailojocic on 2008-05-30
> **dummiebeginner said:**
> My Windows crashed again after another virus and I had to format and reinstall once again. I am desperate.

I tried the different methods you describe here to instll this bl**dy driver in my Esprimo but I just don't know how Linux works and those instructions are chinese to me.

Could somebody please be so kind to explain step by step how to do this? For instance I tried to copy (move) the drivers from the desktop to the drivers folder but it sais it was impossible as I needed administrator privileges. I mean, it's just chinese for any beginner. I've tried a million times and read every manual but still you say things that I don't understand at all (compiling for instance...?¿?¿ what is that?)

Anyone please? Easy step by step instructions as you'd tell your grandmother if she needed them for surviving?

try this

type in terminal

gksudo nautilus and your password

in opened window you can copy those files because you are logged like administrator

linux would not allow you to change any system file if you aren't root user

After that you should change your xorg.conf. This is possible only if you are in root mode so you can also do that in nautilus. Go to /etc/X11/ and you should see xorg.conf file. Open and Add Driver "sis" in Section "Device". Must look like:

```
Section "Device"
              Identifier      "Configured Video Device"
              Driver          "sis"
EndSection
```

(don't forget to save changes)

Linux is grate choice, Ubuntu even better :)

---

### Post by kajaman13 on 2008-05-30
Hi guys,

I have good news. My video RESIZES!!! :-)

I user the driver mihailojocic put on rapidshare (probably Barros Lee stuff) and still no resizing. mihailojocic claimed to have no such problems with it so I had no idea why. Some 5 minutes ago it came to me. He mentioned no 
Option "EnableSiSCtrl" "yes"
Option "XvDefaultAdaptor" "Blitter"
... so the problem could be there. 
I googled them and tried an alternative to "Blitter" -> "Overlay" and the rest is history, so to speak. :-)

This "discovery" might be an old stuf to many of you, but I'm sure that there are still some slower types like me, who haven't put one and one together yet. 

PS: If there are no such people - sorry for bothering you

---

### Post by dummiebeginner on 2008-05-31
> **mihailojocic said:**
> try this

[B]type in terminal

gksudo nautilus and your password[/B]

OK, finally, it worked. That was the missing instruction. 

So, thanks a lot mihailojocic for being so kind, I really appreciate it. Now I found that my wifi is not recognized by Ubuntu and had to come back to Windows to search and learn how to fix it.I guess this Linux learning will be a long long process.

One more thing. Do these drivers work with Kubuntu, Xubuntu or OpenSuse?

Again, THANKS A LOT!!

---

### Post by ahaertig on 2008-05-31
> **dummiebeginner said:**
> 
One more thing. Do these drivers work with Kubuntu, Xubuntu or OpenSuse?


You can use this driver in every Ubuntu 8.04 version but I don't if it will work on Suse. The old driver for Ubuntu 7.04 didn't work properly on Suse 10.3. Everytime I tried to watch a video X-Server crashed. There are other users reporting the same issue. But maybe the new driver will work. Just test it.

---

### Post by dummiebeginner on 2008-05-31
> **ahaertig said:**
> You can use this driver in every Ubuntu 8.04 version

Thank you!

---

### Post by woodpeaker on 2008-05-31
> **rekado said:**
> Barros Lee contacted me directly and send me the binaries of the new driver for Ubuntu 8.04 (32bit). I also asked him for the source code, hope he can send it to me soon.

Chen Chao Yu also replied to my mail but could only provide the already known driver source code which he maintained until November 2007. He told me that SiS signed contracts with other companies which prevents him to publish the OpenGL driver privately; as I understand, though, the driver exists and is distributed to manufacturers. I will contact Haier China soon in order to inquire the 3D driver.

Attached you can find both the binaries Barros Lee send to me and the source code Chen Chao Yu provided.

To use the driver binaries please move sis_drv.* to /usr/lib/xorg/modules/drivers/
and modify your Xorg.conf by adding 'Driver "sis"' in section "Device".

Hope that helps!


EDIT: sorry, the binaries are too big to attach (just some 50kB bigger than the limit) - i could email them to you, though.

Could you please send drivers to ivan [dot] grunev [dog] gmail [dot] com?
Thanks in advance...

---

### Post by picklingonion on 2008-06-01
> **rekado said:**
> Barros Lee contacted me directly and send me the binaries of the new driver for Ubuntu 8.04 (32bit). I also asked him for the source code, hope he can send it to me soon.

Chen Chao Yu also replied to my mail but could only provide the already known driver source code which he maintained until November 2007. He told me that SiS signed contracts with other companies which prevents him to publish the OpenGL driver privately; as I understand, though, the driver exists and is distributed to manufacturers. I will contact Haier China soon in order to inquire the 3D driver.

Attached you can find both the binaries Barros Lee send to me and the source code Chen Chao Yu provided.

To use the driver binaries please move sis_drv.* to /usr/lib/xorg/modules/drivers/
and modify your Xorg.conf by adding 'Driver "sis"' in section "Device".

Hope that helps!


EDIT: sorry, the binaries are too big to attach (just some 50kB bigger than the limit) - i could email them to you, though.

Sadly when I tried to open the archive in Ubuntu 8.04 I got an error report and it would not open. I've been following this forum as I have the same problem as others here. Still do not have a solution.

If you can help please d2s_uk(at)hotmail(dot)com. Thanks

---

### Post by rekado on 2008-06-01
I updated the two files in my previous post. Pls check again.

---

### Post by RobHK on 2008-06-02
> **terrapene said:**
> Well, I contacted this person and told me that a 3D SIS 672 Driver exist, but only can be offered to costumers. As long as SIS is a Chipset manufacturer, its costumers are mainly motherboard builders, not final users. He kindly sends a feisty 2D SIS 672 driver to anyone who asks for it,  I've tried it on my Fujitsu Siemens V5535 and Gutsy and it works fine!!! . Anyway, you can download it from: 
[http://www.badongo.com/file/5319845](http://www.badongo.com/file/5319845)
[http://www.megaupload.com/?d=OO7FNA7X](http://www.megaupload.com/?d=OO7FNA7X)
[http://rapidshare.com/files/72690205/sis_vga_200807_ubuntu_7.04.tgz.html](http://rapidshare.com/files/72690205/sis_vga_200807_ubuntu_7.04.tgz.html)

All you have to do is moving sis_drv.* to /usr/lib/xorg/modules/drivers/ and modify your Xorg.conf from vesa to sis, by typing:

 $sudo dpkg-reconfigure -phigh xserver-xorg .
I'm reopening this thread in the hope that someone who answered earlier may be able to help me :)

The first time I tried this it worked fine on an installation of Mint 4, which is basically Gutsy. I screwed up that setup and am reinstalling, but I am running into the same problem in 3 separate attempts on Gutsy, Hardy and Mint: when I run sudo dpkg-reconfigure -phigh xserver-xorg nothing happens.

I tried vvebbie's suggestion to change the vesa line to sis in xorg.conf, but there is no reference to vesa in my xorg.conf.

A related point: in Gutsy I could find a resolution of 1280x768, which is pretty close and a usable substitute, by going to administration/screens & graphics, but this is missing from Hardy. Is there any way to access this option?

---

### Post by theGerbil on 2008-06-03
Hi, excuse this slightly vague answer as I'm not at my home Linux PC right now but I hope this helps.

I found that running "sudo dpkg-reconfigure -phigh xserver-xorg" didn't set up the correct setting for me but it kind of gave me a blank xorg from where I could setup the correct settings fairly successfully.

I found that once I had setup up the graphics through the GUI the VESA line did exist but replacing the word VESA with sis only broke everything I had just done and GDM wouldn't run at all.

As for the "Screens & Graphics" option (did I get that right?) it isn't on the menus by default but it does exist. You need to go to the gui where you add things into the menu and it's under something like "Applications / Others".

Doing all this I did manage to get a reasonable quality display, albeit I did have to use screen size 1280x800, resolution 1280x786.

I found I got a much better quality display by compiling a driver from the Intel source.

Good luck ...

---

### Post by Claus_ on 2008-06-03
I downloaded SiS672-based-motherboard video Linux drivers from Asus web site in order to try them on my no-Asus notebook.
I say "drivers" becase there are 4 binaries: for Fedora Core 6, Mandriva 2007.1 , Redhat4.4 and Suse 10.1 .
My question is, can I try any of those binaries on Hardy ?
Wich one? Any Suggestions?
Thanks

---

### Post by pjasnos on 2008-06-03
> **rekado said:**
> Yeah, this has been reported in this thread two times before; so now we are three. I don't know of a workaround.

Try removing >  Option          "XvDefaultAdaptor"      "Blitter" from your xorg.conf (or just comment it out by adding a # at the beginning of a line) My device section looks like this:

Section "Device"
        Identifier      "sis671mx"
        Boardname       "dixons-xp"
        Busid           "PCI:1:0:0"
        Driver          "sis"
        Option          "EnableSiSCtrl"         "yes"
        Screen  0
EndSection

dpkg-reconfigure would not help you, because Xorg 7.3 (used in Hardy) should generally autoconfigure itself so Ubuntu maintainers removed the helpful script for changing resolution from the package.

---

### Post by pjasnos on 2008-06-03
> **Claus_ said:**
> I downloaded SiS672-based-motherboard video Linux drivers from Asus web site in order to try them on my no-Asus notebook.
I say "drivers" becase there are 4 binaries: for Fedora Core 6, Mandriva 2007.1 , Redhat4.4 and Suse 10.1 .
My question is, can I try any of those binaries on Hardy ?
Wich one? Any Suggestions?
Thanks

Sorry, most probably won't work as those systems use older Xorg.

---

### Post by Jerzabek39 on 2008-06-04
> **pjasnos said:**
> Sorry, most probably won't work as those systems use older Xorg.

But it could be 3D driver or not..?

---

### Post by picklingonion on 2008-06-07
[
N.b. if you run displayconfig-gtk again, it will say that you are using Vesa, and so will xorg.conf, but that's not true, as X autoconfigures itself to use sis. (displayconfig-gtk is somewhat deprecated in Hardy AFAIK --> see 
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/207409](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/207409)
because of X.org 7.3)[/QUOTE]

QUOTE=pjasnos;4795800]"almost" point and click method:

Get OttoD modified sources (n.b. he posted a link on this thread, but just in case:

[http://ubuntuforums.org/showpost.php?p=4697207&postcount=4](http://ubuntuforums.org/showpost.php?p=4697207&postcount=4)

```
sudo apt-get build-dep xserver-xorg-video-sis

sudo apt-get install displayconfig-gtk

tar -xjf intelsrc.tar.bz2

cd 2d-driver

./configure --prefix=/usr

sudo make install

sudo displayconfig-gtk
```

Click on Graphics Card --> Driver --> Choose driver by name --> sis (Silicon Integrated Systems)

Go back to Screen, click Model and select appropriate resolution from generic (in my case:
 Generic LCD Panel 1280x800), remember to tick widescreen box if your monitor is widescreen

Choose appropriate screen resolution

Done :)

This is the post that sorted the problem. Thanks for the great explanation. The third line of code needs to be changed according to where you put the driver file. Other than that it worked a dream. Can't imagine why I made such hard work of it. I've saved the instructions just in case :)

---

### Post by primijos on 2008-06-09
Hi,

I'm facing the same problems as everybody in this thread, but this time with a "Clevo M720S-B" [Dual Core 1.8Ghz, 2GB RAM, 256 shared with the video card], which includes the same video card (Sis 771/671). Right now I have installed&running the 2D accelerated driver from Barros Lee, but I can observe it is very slow even for simple tasks as scrolling a page inside firefox or switching windows (I almost can watch them resize). I'm using it under ubuntu 8.04

Has anybody got numbers from glxgears in order to compare them? I've ran it a number of times and the max performance I've got so far are 200-206 FPS (which is an order of magnitude slower compared with, for example, an embeded intel on my desktop with direct rendering enabled or four times slower than the same intel embedded card without direct rendering [aprox 900 FPS])

glxinfo says -of course- I'm using Mesa indirect rendering.

I would like to be able to compare the performance of my setup with yours, as long as we all have the same videocard... Also, if anybody has an idea wether DRI can be enabled without 3D support, it would be great (even if this includes source code modifications, maybe we could contact sis -i.e. Barros Lee-: if they agree to release 2D accelerated drivers, maybe they also agreen to release 2D+DRI drivers?)

thanks in advance.

Best,
Jose

---

### Post by rekado on 2008-06-09
I've got about 210fps. Also noticed the horrible performance when scrolling in firefox. I'm still waiting for Haier to provide the OpenGl driver but this might take a long time...

---

### Post by primijos on 2008-06-09
> **rekado said:**
> I've got about 210fps. Also noticed the horrible performance when scrolling in firefox. I'm still waiting for Haier to provide the OpenGl driver but this might take a long time...

Haier? First news about "Haier". Is it another vedor including also the same graphics card in their laptops/rebranded laptops? Have they said they'll publish an OpenGL driver compatible with Xorg and sis 771/671??

Jose

---

### Post by rekado on 2008-06-09
Haier is a big Chinese company doing almost everything to do with consumer electronics. Also a sponsor of the Olympic Games. They have some very nice computers, design is particularly interesting and slick at times (they are best at LCD screens).
I've bought a SiS packed notebook (Haier A20) for my wife some weeks ago and brought up this driver issue at the dealer's place and the official customer support. Will get notice by the day after tomorrow. The dealer already told me that they don't know about Linux support (if you've ever been to China you will understand why: almost every PC runs the very same cracked WinXP; official programs and files require Microsoft software [open office won't work and without IE you're lost!) - but the dealers are not employed by Haier, as is the support center. They will forward my request to some official positions in the company and as Haier is one of the biggest Chinese companies I think they might have enough power to get the drivers from SiS.

Still hoping.

---

### Post by primijos on 2008-06-09
Oh, ok, I see. I've done something similar. I've contacted with Clevo's customer support at UK, USA and Taiwan. Right now I've only had a response from UK, telling me that they don't know about a Linux driver and asking me to ask Sis who they sent the driver to (to which e-mail/person). I know the driver has been delivered because the developer at Sis has confirmed that point to me. Right now I'm waiting for a reply in order to know to which e-mail/person it was delivered, I'll forward that answer to Clevo's customer support to see if they can, at least, release a DRI/3D binary driver (I don't have much hope on this, but its almost free to ask it...)

By the way... a technical question: is DRI possible without 3D acceleration (only with 2D acceleration)?? From what I've read in this post, seems like neither Sis nor any of the manufacturers are delivering 3D capable drivers, but they do with 2D. If DRI was possible with 2D acceleration, it would be a step in order to get more performance in rendering... (of course, full 3D would be what I would expect after paying for the hardware, despite the fact that Linux is not officially supported "but most of our hardware runs perfectly under Linux", quoting from Clevo's user support service e-mail response...)

Best,
Jose

---

### Post by Skaxxo on 2008-06-10
> **mihailojocic said:**
> Here is link to new SiS 671 ubuntu 8.04 driver and short letter from Barros Lee

;-)

[http://rapidshare.com/files/118140763/sis_vga_150508_ubuntu_8.04.tar.bz2.html](http://rapidshare.com/files/118140763/sis_vga_150508_ubuntu_8.04.tar.bz2.html)

Dear all,

Here is our 2d driver for Ubuntu 8.04, you can try it first.
Please move sis_drv.* to /usr/lib/xorg/modules/drivers/
And modify your Xorg.conf
Add Driver "sis" in Section "Device"

Best Regards
Barros Lee

Thanks to Barros Lee and Denner Peterlini who send me this driver


Hello

This drivers don't works for my sis 671/771 under ubuntu 8.04.
I see a "negative" effect color...
Any suggestions?

---

### Post by Peppe_S on 2008-06-10
Hello

I have a Packardbell easynote mx37 ,with the sis motherboard 672.
I have installed Ubuntu 8.04 64bit, now i'm using the vesa driver,but i want the sis driver.
What I have to do?

---

### Post by Jerzabek39 on 2008-06-10
> **Peppe_S said:**
> Hello

I have a Packardbell easynote mx37 ,with the sis motherboard 672.
I have installed Ubuntu 8.04 64bit, now i'm using the vesa driver,but i want the sis driver.
What I have to do?

Can you read the post up from yours..? :rolleyes:

---

### Post by Peppe_S on 2008-06-10
> **Jerzabek39 said:**
> Can you read the post up from yours..? :rolleyes:

the title of the post is for the sis 672... isn't it the correct post? i haven't find anything else...

---

### Post by Skaxxo on 2008-06-11
This is the result with you're drivers:

[http://img165.imageshack.us/img165/3118/10062008cx9.jpg](http://img165.imageshack.us/img165/3118/10062008cx9.jpg)

It's 1024x800 with negative colors!

---

### Post by rekado on 2008-06-12
The manufacturer of my SiS packed laptop (Haier) replied saying that they cannot provide the driver due to contractual constraints, i.e. they would have to pay some money to SiS if they would like to have the linux drivers. Sounds ridiculous to me, so I will ask again... I paid for the hardware and can't use it. So annoying, especially when the driver does exist!

---

### Post by Skaxxo on 2008-06-12
Can you send me a correct driver for sis 671/771 for ubuntu 8.04 here? 
[IMG]http://services.nexodyne.com/email/icon/D1qrgJygrYtm0CJgJg%3D%3D/ArpZDt8%3D/R01haWw%3D/0/image.png[/IMG]

thanks

---

### Post by darfgarf on 2008-06-14
I've got a novatech laptop using the M672 chip, using this driver and method i can get to the selecting the driver part, but if i select the sis driver, or any other for that matter, and onfigure the display settings correctly, when i click test i get green vertical lines across the top of the screen and the failed message, i'm using 8.04 hardy (most recent).

was this the right driver to attempt, or am i just doing something really stupid.


...still better than windows...

---

### Post by superconny on 2008-06-14
I've successfully installed the sis_vga_drv_150508 driver on my Esprimo Mobile, and it works well only with following restrictions:
- If I use Defaultdepth 24 in xorg.conf, the desktop looks qite good, but I believe it has a aximum of 16 bit for colors.
- If I use Defaultdepth 8 or 16, and I made a warm boot after Windows XP was running previously, I get a desktop with probably 8 or 24 bit colors, so using Defaultdepth 16 results in an optimal look. But if I made a cold boot (computer had been switched off for some seconds, and Windows has not been booted before, I only jitters terrible, and nothing (except the mouse cursor) can be recognized. Has anybody an idea what there's wrong?

---

### Post by darfgarf on 2008-06-15
ok you can ignore me now, managed to get the dam thing working, by going into change resolution after selecting the right driver/monitor combination, duh!

don't suppose anyone's managed to get the M672 working with direct rendering in 8.04 have they?

---

### Post by rekado on 2008-06-15
the color depth doesnt look like 24 bits on my notebook either.

---

### Post by sayid on 2008-06-15
Hello,

I think that 2D driver with Barros Lee's driver is working (not with a simple configure, make install, but it's working).

I've searched in lots of web pages for a 3D solution, but not exist anything.

In previous post I asked if any person here knows how to ask ubuntu's developers include any 3D version of this driver in futures releases but  until now I 've not have any answer.

Other possibility (that I discarded)  was ask for drivers in SiS company, but they NEVER' ll give as drivers for our hardware :(.

Have any some idea? 
Sayid...

---

### Post by darfgarf on 2008-06-15
yep 2D works ok, no aceleration or anything for me yet...any ideas?

sis won't give the drivers, i asked novtech support as thats where i got the laptop and they just pointed me here lol so it's unlikely that anyones going to give out the driver.

...could get a job with sis and steal the file maybe...

---

### Post by sayid on 2008-06-15
> **darfgarf said:**
> yep 2D works ok, no aceleration or anything for me yet...any ideas?

sis won't give the drivers, i asked novtech support as thats where i got the laptop and they just pointed me here lol so it's unlikely that anyones going to give out the driver.

...could get a job with sis and steal the file maybe...

Jaja, you're right darfgarf, but if we see the things with other eyes, SiS is stealing us, because we are paying for 3D aceleration not for 2D.

Perhaps with some Barros Lee friend can help us ;).

Have any in this forum idea in RE existing drivers?

Can anybody help me sending a request to ubuntu developers with this issue?

Sayid...

---

### Post by Claus_ on 2008-06-16
> **sayid said:**
> Jaja, you're right darfgarf, but if we see the things with other eyes, SiS is stealing us, because we are paying for 3D aceleration not for 2D.

Perhaps with some Barros Lee friend can help us ;).

Have any in this forum idea in RE existing drivers?

Can anybody help me sending a request to ubuntu developers with this issue?

Sayid...

I wrote to all ECS/Uniwill adresses (most are invalid) and the response was "No drivers for you !!   Next !!"  
Amy Nguyen from ECS USA said that they don't have any drivers for "Linus" (SIC)
I've installed the Barros Lee drivers with no noticeable change.

---

### Post by superconny on 2008-06-16
Good news! After upgrading the bios of the Esprimo Mobile V5535 to version 1.06 from 2008-05-30, the problems with 2D driver have been solved. Even if XP had been started before, no jitter can be seen on the display now, even if Colordepth is 8, 16 or 24. Only little error: 16 and 24 seem to be exchanged, for best picture use 16.

---

### Post by sayid on 2008-06-17
> **Claus_ said:**
> I wrote to all ECS/Uniwill adresses (most are invalid) and the response was "No drivers for you !!   Next !!"  
Amy Nguyen from ECS USA said that they don't have any drivers for "Linus" (SIC)
I've installed the Barros Lee drivers with no noticeable change.

Hello Claus, It seems a xorg.conf setting problem, can you post here the output of cat /etc/X11/xorg.conf? I modify a little this file and the changes were showed :).

I've received a little mail from Barros Lee, the answer is always the same, "Although I am the developer of SiS671 linux 3D driver, I have no rights to send it to you right now. Because SiS don't allowed me to do that...". After he said: "...If you want to get latest SiS linux 3d driver, you can contact your motherboard vendor..." 

This comment was seen for me in other posts with negative results. Perhaps your motherboard vendor'll give you the drivers and after this the open source community and me will be very very happy :D.

Regards,
Sayid...

---

### Post by debianite on 2008-06-17
One thing that might help, would be the guys who have the driver working, to post their xorg.conf and the system they are using.
I noticed that some times the cause for the driver not working properly is the just bad xorg.conf configuration. I don't have my crappy sis laptop with me at the moment but i will post my config as soon is i have it.

Here it is, this is on a Fujitsu Siemens Esprimo 5515

```
# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"pt"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "Device"
	Identifier	"Generic Video Card"
	Driver		"sis"
	BusID		"PCI:1:0:0"
	Option		"EnableSiSCtrl"		"yes"
	Option		"XvDefaultAdaptor"	"Overlay"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
	Modes		"1200x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice	"Synaptics Touchpad"
EndSection
```

---

### Post by Dennis Schulmeister on 2008-06-17
Hi all,

I just think you should read this: [http://barroslee.blogspot.com/2008/05/its-time-to-leave-sis.html](http://barroslee.blogspot.com/2008/05/its-time-to-leave-sis.html). Obviously Barros Lee won't stay at SiS any longer than 'til September.

BTW: I had quite good success with the OttoD patched drivers but there are still some black vertical lines in the upper screen area. (SiS m672 in a Fujitsu-Siemens Esprimo ...). Frankly I've been trying for two days now and it's getting frustrating.

What's even more iritating is that those vertical lines do disapear of you once switch to a framebuffer console and back (Alt+F1, Alt+F7). That'd be fine enough for me. But not for my mother whom the laptop belongs to and who is a computer illiterate as many mothers out there. :)

Dennis

---

### Post by Dennis Schulmeister on 2008-06-17
BTW: Can you please stop using that silly RapidShare. The free download account has a rather ambiguous captcha and so it's quite impossible to GUESS the captcha letters.

Here's an offer. Anybody who wants to share SiS drivers or the like with the community can send them to me and I'll put them on my small but always working home server. ([http://ncc-1701a.homelinux.net](http://ncc-1701a.homelinux.net)). Or if you want you can get your own account on the machine and upload the files yourself.

Dennis

---

### Post by Claus_ on 2008-06-17
> **sayid said:**
> Hello Claus, It seems a xorg.conf setting problem, can you post here the output of cat /etc/X11/xorg.conf? I modify a little this file and the changes were showed :).

I've received a little mail from Barros Lee, the answer is always the same, "Although I am the developer of SiS671 linux 3D driver, I have no rights to send it to you right now. Because SiS don't allowed me to do that...". After he said: "...If you want to get latest SiS linux 3d driver, you can contact your motherboard vendor..." 

This comment was seen for me in other posts with negative results. Perhaps your motherboard vendor'll give you the drivers and after this the open source community and me will be very very happy :D.

Regards,
Sayid...

Sure, this is my xconf.org

```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"latam"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"VESA driver (generic)"
	Busid		"PCI:1:0:0"
	Driver		"sis"
	Screen	0
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x800"
	Horizsync	31.5-50.0
	Vertrefresh	56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	800
		Modes		"1280x768@60"	"1280x720@60"	"800x600@60"	"1280x800@60"	"800x600@56"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" #   
	Identifier	"device1"
	Boardname	"VESA driver (generic)"
	Busid		"PCI:1:0:0"
	Driver		"sis"
	Screen	1
EndSection
Section "screen" #   
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
	SubSection "Display"
		Depth	24
		Modes		"640x480@60"
	EndSubSection
EndSection
Section "monitor" #   
	Identifier	"monitor1"
	Vendorname	"Plug 'n' Play"
	Modelname	"Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection
```

It works as good as the original VESA driver. I hope I was able to turn on some visual effects.
Claus

---

### Post by jeracravo on 2008-06-17
Ok guys,

Sorry, I know it´s a newbie question but I have to ask it:

I downloaded the file from Barros Lee but when I try to drag the files into the /usr/....../drivers folder, the OS says I don´t have permission to do this.

How do I do this?

I just bought a laptop to use Ubuntu on it (I´ve used on a friend computer and I loved it!! By the way, my other computer is a mac...) but my wireless card and my graphic card aren´t working proprely.

Thanks for your time!

---

### Post by debianite on 2008-06-18
> **jeracravo said:**
> Ok guys,

Sorry, I know it´s a newbie question but I have to ask it:

I downloaded the file from Barros Lee but when I try to drag the files into the /usr/....../drivers folder, the OS says I don´t have permission to do this.

How do I do this?

I just bought a laptop to use Ubuntu on it (I´ve used on a friend computer and I loved it!! By the way, my other computer is a mac...) but my wireless card and my graphic card aren´t working proprely.

Thanks for your time!

I have to copy them as the root user.

---

### Post by XenuHubbard on 2008-06-18
Hi everyone -- this seems to be *the* Internet thread for posting/griping about SiS and their proprietary garbage.  I too have been having the same problems with my laptop's SiS M672...I now have the drivers installed, and my xorg.conf seems to be right.  Except, I have the same problem as Skaxxo above, namely the colors are all in 'negative': I'm not sure which is more hideous, 800x600 blockiness or 1280x800 in psychedelics.
 
Being something of a masochist, I am using Lunar Linux.  I think that the problem may be one of version incompatibility with Xorg, in that plain text web pages seem to display OK, but it is the little window accoutrements which are the most affected by the colour problems.

*So, I am wondering if anyone with a working configuration can post what version number they have of Xorg, glibc, cairo, [COLOR="Red"]gtk(+2)[/COLOR] (I think that might be the culprit) and any other relevant packages they can think of?  I have the drivers for both Ubuntu 7 and 8, so either setup could work, if I know which versions of other packages to download and compile.*

Or if there are any other driver versions lurking around (someone mentioned Mandriva or Slackware or something), if anyone who feels like posting those along with the versions of the relevant packages.

Thanks for any assistance!

@Dennis: You mentioned using your server to host files relevant to this...why not upload all the versions of the drivers to there, then there is at least a central repository for other wayfarers who come by this thread, without having to wade through pages of nonsense and negotiate horrible captchas?  It would be a valuable public service!

---

### Post by jeracravo on 2008-06-18
> **debianite said:**
> I have to copy them as the root user.

And how do I do this?

---

### Post by XenuHubbard on 2008-06-18
> **jeracravo said:**
> And how do I do this?

Open a terminal (i.e. 'command prompt')

type in ```
su
``` and enter your (root) password

then type in ```
cp /directory/where/you/put/them/* /usr/lib/xorg/modules/drivers
```

then ```
exit
``` to get out of superuser mode

Alternatively, you could try it in one step, viz.:

```
sudo cp /directory/where/you/put/them/* /usr/lib/xorg/modules/drivers
```

Hope this helps -- I'm not sure how Ubuntu's set up, but the above should be pretty generic.  If you saved the drivers to your desktop, then the directory is probably something like /home/YourUsername/Desktop.

I know using a command line may seem like a pain when you're used to a window system, but it can actually be quicker once you get used to it: there is probably another way you can do the above, by logging out of your desktop as a user, logging in as root, copying using the drag/drop file manager, logging out...you see my point.

*Edited to add:* Another option is to open the terminal, and type in 'sudo' followed by the name of whatever file manager you use (e.g. 'konqueror'), then enter the root password -- which I'd guess you chose when installing -- and do the drag and drop copy.

---

### Post by jeracravo on 2008-06-18
Thanks a lot Xenu,
I got it right.
One more question.
How do I change my xorg.conf file?
All text editors won't let me save the changes to the file.
Should I save it with another name on the desktop, then rename it and then copy it to it's original place?
Thanks again!

---

### Post by XenuHubbard on 2008-06-18
> **jeracravo said:**
> Thanks a lot Xenu,
I got it right.
One more question.
How do I change my xorg.conf file?
All text editors won't let me save the changes to the file.
Should I save it with another name on the desktop, then rename it and then copy it to it's original place?
Thanks again!

No problem.  

The best way to edit your xorg.conf would probably be to follow a similar procedure to the above: go to a terminal, and type in 'sudo' followed by the name of whatever text editor you use (I think Ubuntu runs on Gnome, so try 'sudo gedit').  Then work on the file, and you should be able to save.

Else yes, you can just save it anywhere, then go in as root/superuser and copy it to the right spot (/etc/X11/xorg.conf, usually), following the same technique as you used with the drivers.

---

### Post by jeracravo on 2008-06-18
Ok,

the 'sudo gedit /etc/x11/xorg.conf' gave me a clean text file...
so I went and onpened the original xorg.conf file, changed what I needed and saved it without a problem.
now I understand after you open the application with the 'sudo' command, it stays with the privileges even if you open another file right?
anyways, now I can use 1280x800 on my laptop, so it's fine with me!
now, just need to make the wireless card work...
thanks a lot guys!!!

---

### Post by Claus_ on 2008-06-18
> **jeracravo said:**
> And how do I do this?

You can also type in a terminal:

SUDO NAUTILUS

Be careful

---

### Post by andreabu on 2008-06-18
It seems the new kernel 2.6.25 is going to support the sis 671 boards as seen here: 

[http://kernelnewbies.org/Linux_2_6_25#head-9becf0d7793603055f44d7414f91bfe1d44fb59e](http://kernelnewbies.org/Linux_2_6_25#head-9becf0d7793603055f44d7414f91bfe1d44fb59e)

we will just have to wait until it reaches our distros...
Not sure about the 3d support though...

---

### Post by XenuHubbard on 2008-06-18
> **andreabu said:**
> It seems the new kernel 2.6.25 is going to support the sis 671 boards as seen here: 

[http://kernelnewbies.org/Linux_2_6_25#head-9becf0d7793603055f44d7414f91bfe1d44fb59e](http://kernelnewbies.org/Linux_2_6_25#head-9becf0d7793603055f44d7414f91bfe1d44fb59e)

we will just have to wait until it reaches our distros...
Not sure about the 3d support though...

Running a 2.6.25.7 kernel at the moment...it seems that the update is simply a patch to allow the 671 card to be detected, and possibly to work with a framebuffer for a text console.  I remember seeing the diffs somewhere, though I don't remember the full details -- they were submitted by Cheong (sp.?) from SiS.  Unfortunately, they don't help for xorg, and they certainly aren't 3D!

Can no-one post version numbers of xorg, gtk(2), cairo, etc. on a working configuration for me, as per my above post?  Please? I'm at my wits' end with this thing, and I cannot face wading through package repositories trying to decide what versions were shipped with particular distributions; or, a link to the exact versions shipped with Ubuntu Feisty or Hardy would do just the same thing, but I can't seem to find them anywhere.  I've been at this too long, methinks...

---

### Post by Dennis Schulmeister on 2008-06-18
OK, here you go: [http://ncc-1701a.homelinux.net/WikiBerd/index.php?page=LinuxSis67x](http://ncc-1701a.homelinux.net/WikiBerd/index.php?page=LinuxSis67x)

That's basicaly all information and all files I could gather from this thread plus some of my own experience.

Please help me to keep this thing up to date. Instead of uploading any file to such non-working and dubious services like RapidShare just send them to me and I'll put them on the server. The same goes for any information, of course.

Dennis (dennis -at- ncc-1701a.homelinux.net)

---

### Post by jeracravo on 2008-06-18
Well,

I at least could get my monitor to work with the right resolution.
But without 3D and without my wireless I think I´ll have to pass Ubuntu for now.
I´ll install Windows XP until I can get a good distro that works with my chipset.

---

### Post by Dennis Schulmeister on 2008-06-18
Now I got it. The garbage lines are gone for sure. :guitar:

The problem was the kernel framebuffer. I added vga=0x0318 to the kernel boot parameters in order to get a nice and large console. Well it turned out that this confused some graphic registers and without that option everything works fine.

Downside is that the large console hs shrunked to default mini size ...

Dennis

---

### Post by XenuHubbard on 2008-06-19
> **Dennis Schulmeister said:**
> OK, here you go: [http://ncc-1701a.homelinux.net/WikiBerd/index.php?page=LinuxSis67x](http://ncc-1701a.homelinux.net/WikiBerd/index.php?page=LinuxSis67x)

That's basicaly all information and all files I could gather from this thread plus some of my own experience.

Please help me to keep this thing up to date. Instead of uploading any file to such non-working and dubious services like RapidShare just send them to me and I'll put them on the server. The same goes for any information, of course.

Dennis (dennis -at- ncc-1701a.homelinux.net)

Thanks -- that looks superb.  I emailed you the 64-bit drivers that you're missing there, but sent them to the windows3.de account listed on that website...I only noticed your address here later.  Just thought to let you know.

---

### Post by Dennis Schulmeister on 2008-06-19
Hi Stephen (Xenu),

got your mail. Appreciated it a lot.

Dennis

---

### Post by sayid on 2008-06-19
Hello Denis Schulmeister, I have read your web, it's an excellent start point, perhaps in some days any experimental 3D driver appears. 

I mailed Barros Lee for a solution, of course the mail only explains always the same sad history :(.

But in some part of the mail he said ".If you want to get latest SiS linux 3d driver, you can contact your motherboard vendor.". Well I never mailed Intel or other vendor that use this chipset. 

My question is, any of this forum mailed them?

---

### Post by Dennis Schulmeister on 2008-06-19
> **sayid said:**
> Hello Denis Schulmeister, I have read your web, it's an excellent start point, perhaps in some days any experimental 3D driver appears. 

I mailed Barros Lee for a solution, of course the mail only explains always the same sad history :(.

But in some part of the mail he said ".If you want to get latest SiS linux 3d driver, you can contact your motherboard vendor.". Well I never mailed Intel or other vendor that use this chipset. 

My question is, any of this forum mailed them?

I'm glad you like the site.

In fact many people have contacted their MoBo / notebook Mfctrs. Without much success, though. (See page 1 onwards of this thread).

Dennis

---

### Post by sayid on 2008-06-19
> **Dennis Schulmeister said:**
> I'm glad you like the site.

In fact many people have contacted their MoBo / notebook Mfctrs. Without much success, though. (See page 1 onwards of this thread).

Dennis

Yeah! I have read this thread more than once time.

I think that we should have two solutions:

1) Do RE over the windows drivers (disadvantages: lots of work, few people with this problem, etc) 

2) Wait ubuntu's developers team include this driver in future works.

---

### Post by XenuHubbard on 2008-06-19
Well, I tried something completely different: Arch Linux running in 64 bit.  Still the same strange problem with 'reversed' colours...I am not so sure it is a versioning problem anymore...

The colours aren't exactly reversed, however.  Playing around with the palette in the Gimp, it seems that the following is happening:
[LIST]
[*]Green channel is fine, but red and blue have problems
[*]Thus, what should be a generic grey window colour when, say, loading up Firefox under a plain x server, is magenta instead
[*]In particular, it seems that the colours are 'cycling': instead of the usual spectrum for picking a colour, there are four bands which more or less repeat
[*]But these bands do not blend -- like a spectrum -- being instead bars of discrete colours
[/LIST]

Is this some sort of endian issue on the R and B channels, does anyone think?  It seems to be that, or something to do with subpixel rendering...

Any ideas?

---

### Post by subiet on 2008-06-25
bump for 3d

---

### Post by Father D on 2008-06-26
What a crap company Sis is! .. anyway..
I have managed to get the 64bit Mandriva 2D driver working on my Fedora 8 x64
with one small hitch! there is a strange colour artifact for a second or so at the beginning of the x-server, it does not continue once the boot logging/log-in starts , but appears every time the x-server is initiated.

Any ideas??

Here is my xorg.conf and xorg log:

xorg.conf
-----------------------------
# Xorg configuration created by system-config-display

Section "ServerLayout"
	Identifier     "single head configuration"
	Screen         "Screen0" 0 0
	InputDevice    "Keyboard0" "CoreKeyboard"
	InputDevice    "Synaptics" "CorePointer"
EndSection

Section "Module"
	Load	        "dbe"
	Load	        "extmod"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "gb"
EndSection

Section "InputDevice"
	Identifier  "Synaptics"
	Driver      "synaptics"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "auto-dev"
	Option	    "Emulate3Buttons" "yes"
EndSection

Section "Monitor"
	Identifier   "Generic LCD Panel"
	VendorName   "Generic LCD Display"
	ModelName    "LCD Panel 1280x800"
	Option       "DPMS"
EndSection

Section "Device"
	Identifier  "[M]671/[M]771[GX]"
	Driver      "sis"
	BusID       "PCI:1:0:0"
	Option	    "XvDefaultAdaptor"	"Overlay"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "[M]671/[M]771[GX]"
	Monitor    "Generic LCD Panel"
	DefaultDepth     24
        SubSection "Display"
		Depth     8
		Modes     "1280x800"
        EndSubSection
        SubSection "Display"
		Depth     16
		Modes     "1280x800"
        EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes	 "1280x800"
	EndSubSection
EndSection
---------------------------------------
---------------------------------------
xorg.log
---------------------------------------

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Fedora 8 Red Hat, Inc.
Current Operating System: Linux Vigor12 2.6.25.6-27.fc8 #1 SMP Fri Jun 13 16:17:54 EDT 2008 x86_64
Build Date: 11 June 2008
Build ID: xorg-x11-server 1.3.0.0-46.fc8 
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Jun 26 09:37:21 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "single head configuration"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Generic LCD Panel"
(**) |   |-->Device "[M]671/[M]771[GX]"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Synaptics"
(II) No default mouse found, adding one
(**) |-->Input Device "<default pointer>"
(WW) No FontPath specified.  Using compiled-in default.
(==) FontPath set to:
	catalogue:/etc/X11/fontpath.d,
	built-ins
(==) RgbPath set to "/usr/share/X11/rgb"
(==) ModulePath set to "/usr/lib64/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x7be860
(II) Module ABI versions:
	X.Org ANSI C Emulation: 0.3
	X.Org Video Driver: 1.2
	X.Org XInput driver : 0.7
	X.Org Server Extension : 0.3
	X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib64/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 1039,0671 card 1019,5050 rev 00 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 1039,0003 card 0000,0000 rev 00 class 06,04,00 hdr 01
(II) PCI: 00:02:0: chip 1039,0968 card 1019,5a00 rev 01 class 06,01,00 hdr 80
(II) PCI: 00:02:5: chip 1039,5513 card 1019,5a00 rev 01 class 01,01,80 hdr 00
(II) PCI: 00:03:0: chip 1039,7001 card 1019,5a00 rev 0f class 0c,03,10 hdr 80
(II) PCI: 00:03:1: chip 1039,7001 card 1019,5a00 rev 0f class 0c,03,10 hdr 00
(II) PCI: 00:03:3: chip 1039,7002 card 1019,5a00 rev 00 class 0c,03,20 hdr 00
(II) PCI: 00:04:0: chip 1039,0191 card 1019,5a00 rev 02 class 02,00,00 hdr 00
(II) PCI: 00:05:0: chip 1039,1183 card 1039,1183 rev 03 class 01,01,8f hdr 00
(II) PCI: 00:0f:0: chip 1039,7502 card 1019,5a00 rev 00 class 04,03,00 hdr 00
(II) PCI: 01:00:0: chip 1039,6351 card 1019,5050 rev 10 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000c (VGA_EN is set)
(II) Bus 1 I/O range:
	[0] -1	0	0x00009000 - 0x000090ff (0x100) IX[B]
	[1] -1	0	0x00009400 - 0x000094ff (0x100) IX[B]
	[2] -1	0	0x00009800 - 0x000098ff (0x100) IX[B]
	[3] -1	0	0x00009c00 - 0x00009cff (0x100) IX[B]
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xb0000000 - 0xb00fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:2:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter rev 16, Mem @ 0xc0000000/28, 0xb0000000/17, I/O @ 0x9000/7
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x100000000) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xa0000000 from 0xafffffff to 0x9fffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xb0100000 - 0xb0103fff (0x4000) MX[B]
	[1] -1	0	0xb0307000 - 0xb030707f (0x80) MX[B]
	[2] -1	0	0xb0106000 - 0xb0106fff (0x1000) MX[B]
	[3] -1	0	0xb0105000 - 0xb0105fff (0x1000) MX[B]
	[4] -1	0	0xb0104000 - 0xb0104fff (0x1000) MX[B]
	[5] -1	0	0xa0000000 - 0x9fffffff (0x0) MX[B]O
	[6] -1	0	0xb0000000 - 0xb001ffff (0x20000) MX[B](B)
	[7] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[8] -1	0	0x000010a0 - 0x000010af (0x10) IX[B]
	[9] -1	0	0x000010b8 - 0x000010bb (0x4) IX[B]
	[10] -1	0	0x000010c0 - 0x000010c7 (0x8) IX[B]
	[11] -1	0	0x000010bc - 0x000010bf (0x4) IX[B]
	[12] -1	0	0x000010c8 - 0x000010cf (0x8) IX[B]
	[13] -1	0	0x00001000 - 0x0000107f (0x80) IX[B]
	[14] -1	0	0x00001080 - 0x0000108f (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x00009000 - 0x0000907f (0x80) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xb0100000 - 0xb0103fff (0x4000) MX[B]
	[1] -1	0	0xb0307000 - 0xb030707f (0x80) MX[B]
	[2] -1	0	0xb0106000 - 0xb0106fff (0x1000) MX[B]
	[3] -1	0	0xb0105000 - 0xb0105fff (0x1000) MX[B]
	[4] -1	0	0xb0104000 - 0xb0104fff (0x1000) MX[B]
	[5] -1	0	0xa0000000 - 0x9fffffff (0x0) MX[B]O
	[6] -1	0	0xb0000000 - 0xb001ffff (0x20000) MX[B](B)
	[7] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[8] -1	0	0x000010a0 - 0x000010af (0x10) IX[B]
	[9] -1	0	0x000010b8 - 0x000010bb (0x4) IX[B]
	[10] -1	0	0x000010c0 - 0x000010c7 (0x8) IX[B]
	[11] -1	0	0x000010bc - 0x000010bf (0x4) IX[B]
	[12] -1	0	0x000010c8 - 0x000010cf (0x8) IX[B]
	[13] -1	0	0x00001000 - 0x0000107f (0x80) IX[B]
	[14] -1	0	0x00001080 - 0x0000108f (0x10) IX[B]
	[15] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[16] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[17] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[18] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[19] -1	0	0x00009000 - 0x0000907f (0x80) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xb0100000 - 0xb0103fff (0x4000) MX[B]
	[5] -1	0	0xb0307000 - 0xb030707f (0x80) MX[B]
	[6] -1	0	0xb0106000 - 0xb0106fff (0x1000) MX[B]
	[7] -1	0	0xb0105000 - 0xb0105fff (0x1000) MX[B]
	[8] -1	0	0xb0104000 - 0xb0104fff (0x1000) MX[B]
	[9] -1	0	0xa0000000 - 0x9fffffff (0x0) MX[B]O
	[10] -1	0	0xb0000000 - 0xb001ffff (0x20000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x000010a0 - 0x000010af (0x10) IX[B]
	[15] -1	0	0x000010b8 - 0x000010bb (0x4) IX[B]
	[16] -1	0	0x000010c0 - 0x000010c7 (0x8) IX[B]
	[17] -1	0	0x000010bc - 0x000010bf (0x4) IX[B]
	[18] -1	0	0x000010c8 - 0x000010cf (0x8) IX[B]
	[19] -1	0	0x00001000 - 0x0000107f (0x80) IX[B]
	[20] -1	0	0x00001080 - 0x0000108f (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00009000 - 0x0000907f (0x80) IX[B](B)
(II) LoadModule: "dbe"
(II) Loading /usr/lib64/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "extmod"
(II) Loading /usr/lib64/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "sis"
(II) Loading /usr/lib64/xorg/modules/drivers//sis_drv.so
(II) Module sis: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 0.8.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 1.0
(II) LoadModule: "kbd"
(II) Loading /usr/lib64/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "synaptics"
(II) Loading /usr/lib64/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
	compiled for 4.3.99.902, module version = 1.0.0
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib64/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.3
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 0.7
(II) SIS: driver for SiS chipsets: SIS5597/5598, SIS530/620,
	SIS6326/AGP/DVD, SIS300/305, SIS630/730, SIS540, SIS315, SIS315H,
	SIS315PRO/E, SIS550, SIS650/M650/651/740, SIS330(Xabre),
	SIS[M]661[F|M]X/[M]741[GX]/[M]760[GX]/[M]761[GX]/662, SIS340,
	[M]670/[M]770[GX], [M]671/[M]771[GX]
(II) SIS: driver for XGI chipsets: Volari Z7 (XG20),
	Volari V3XT/V5/V8/Duo (XG40/XG42)
(II) Primary Device is: PCI 01:00:0
(--) Chipset [M]671/[M]771[GX] found
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xb0100000 - 0xb0103fff (0x4000) MX[B]
	[5] -1	0	0xb0307000 - 0xb030707f (0x80) MX[B]
	[6] -1	0	0xb0106000 - 0xb0106fff (0x1000) MX[B]
	[7] -1	0	0xb0105000 - 0xb0105fff (0x1000) MX[B]
	[8] -1	0	0xb0104000 - 0xb0104fff (0x1000) MX[B]
	[9] -1	0	0xa0000000 - 0x9fffffff (0x0) MX[B]O
	[10] -1	0	0xb0000000 - 0xb001ffff (0x20000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x000010a0 - 0x000010af (0x10) IX[B]
	[15] -1	0	0x000010b8 - 0x000010bb (0x4) IX[B]
	[16] -1	0	0x000010c0 - 0x000010c7 (0x8) IX[B]
	[17] -1	0	0x000010bc - 0x000010bf (0x4) IX[B]
	[18] -1	0	0x000010c8 - 0x000010cf (0x8) IX[B]
	[19] -1	0	0x00001000 - 0x0000107f (0x80) IX[B]
	[20] -1	0	0x00001080 - 0x0000108f (0x10) IX[B]
	[21] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[22] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[23] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[25] -1	0	0x00009000 - 0x0000907f (0x80) IX[B](B)
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xb0100000 - 0xb0103fff (0x4000) MX[B]
	[5] -1	0	0xb0307000 - 0xb030707f (0x80) MX[B]
	[6] -1	0	0xb0106000 - 0xb0106fff (0x1000) MX[B]
	[7] -1	0	0xb0105000 - 0xb0105fff (0x1000) MX[B]
	[8] -1	0	0xb0104000 - 0xb0104fff (0x1000) MX[B]
	[9] -1	0	0xa0000000 - 0x9fffffff (0x0) MX[B]O
	[10] -1	0	0xb0000000 - 0xb001ffff (0x20000) MX[B](B)
	[11] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[12] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[13] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[14] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[15] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[16] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[17] -1	0	0x000010a0 - 0x000010af (0x10) IX[B]
	[18] -1	0	0x000010b8 - 0x000010bb (0x4) IX[B]
	[19] -1	0	0x000010c0 - 0x000010c7 (0x8) IX[B]
	[20] -1	0	0x000010bc - 0x000010bf (0x4) IX[B]
	[21] -1	0	0x000010c8 - 0x000010cf (0x8) IX[B]
	[22] -1	0	0x00001000 - 0x0000107f (0x80) IX[B]
	[23] -1	0	0x00001080 - 0x0000108f (0x10) IX[B]
	[24] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[25] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[26] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[28] -1	0	0x00009000 - 0x0000907f (0x80) IX[B](B)
	[29] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[30] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(II) Enabling PCI device
(II) SIS(0): SiS driver (2006/10/17-1, compiled for X.org 7.1.1.0)
(II) SIS(0): Copyright (C) 2001-2005 Thomas Winischhofer <thomas@winischhofer.net> and others
(II) SIS(0): *** See [http://www.winischhofer.at/linuxsisvga.shtml](http://www.winischhofer.at/linuxsisvga.shtml)
(II) SIS(0): *** for documentation, updates and a Premium Version.
(II) SIS(0): RandR rotation support not available in this version.
(II) SIS(0): Dynamic modelist support not available in this version.
(II) SIS(0): Screen growing support not available in this version.
(II) SIS(0): Advanced Xv video blitter not available in this version.
(II) SIS(0): Advanced MergedFB support not available in this version.
(--) SIS(0): sisfb not found
(--) SIS(0): Relocated I/O registers at 0x9000
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"(II) Module already built-in
(**) SIS(0): Depth 24, (--) framebuffer bpp 32
(==) SIS(0): RGB weight 888
(==) SIS(0): Default visual is TrueColor
(--) SIS(0): Video BIOS version "3.72.02" found (new SiS data layout)
(**) SIS(0): Option "XvDefaultAdaptor" "Overlay"
(==) SIS(0): Using XAA acceleration architecture
(==) SIS(0): Color HW cursor is enabled
(II) SIS(0): Using VRAM command queue, size 512k
(==) SIS(0): Hotkey display switching is enabled
(==) SIS(0): SiSCtrl utility interface is disabled
(II) SIS(0): For information on SiSCtrl, see
		[http://www.winischhofer.at/linuxsispart1.shtml#sisctrl](http://www.winischhofer.at/linuxsispart1.shtml#sisctrl)
(==) SIS(0): X server will not keep DPI constant for all screen sizes
(==) SIS(0): DRI enabled
(--) SIS(0): 131072K shared video RAM (UMA)
(--) SIS(0): DRAM type: DDR SDRAM
(--) SIS(0): Memory clock: 596.582 MHz
(--) SIS(0): DRAM bus width: 64 bit
(--) SIS(0): Linear framebuffer at 0xC0000000
(--) SIS(0): MMIO registers at 0xB0000000 (size 64K)
(--) SIS(0): VideoRAM: 131072 KB
(II) SIS(0): Using 20480K of framebuffer memory at offset 0K
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"(II) Module already built-in
(--) SIS(0): Detected SiS307LV video bridge (Charter/UMC-1, ID 7; Rev 0xe1)
(--) SIS(0): No CRT1/VGA detected
(--) SIS(0): Detected LCD/plasma panel (1280x800, 14, non-exp., RGB24 [ec0205])
(==) SIS(0): Using gamma correction (1.0, 1.0, 1.0)
(II) SIS(0): CRT1 gamma correction is enabled
(II) SIS(0): Separate Xv gamma correction for CRT1 is disabled
(II) SIS(0): CRT2 gamma correction is enabled
(--) SIS(0): Memory bandwidth at 32 bpp is 1193.16 MHz
(--) SIS(0): Detected LCD PanelDelayCompensation 0x00 (for LCD=CRT1)
(--) SIS(0): 302LV/302ELV: Using EMI 0x0a000002 (LCD)
(--) SIS(0): CRT2 DDC probing failed
(==) SIS(0): Min pixel clock is 10 MHz
(--) SIS(0): Max pixel clock is 340 MHz
(II) SIS(0): Replaced entire mode list with built-in modes
(II) SIS(0): Correcting missing CRT2 monitor HSync range
(II) SIS(0): Correcting missing CRT2 monitor VRefresh range
(II) SIS(0): "Unknown reason" in the following list means that the mode
(II) SIS(0): is not supported on the chipset/bridge/current output device.
(II) SIS(0): Generic LCD Panel: Using hsync range of 30.00-80.00 kHz
(II) SIS(0): Generic LCD Panel: Using vrefresh range of 59.00-61.00 Hz
(II) SIS(0): Generic LCD Panel: Using vrefresh value of 71.00 Hz
(II) SIS(0): Clock range:  10.00 to 340.00 MHz
(II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
(II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
(II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
(II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
(II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
(II) SIS(0): Not using default mode "800x600" (vrefresh out of range)
(II) SIS(0): Not using default mode "800x600" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "640x480" (vrefresh out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "640x480" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (vrefresh out of range)
(II) SIS(0): Not using default mode "1024x768" (vrefresh out of range)
(II) SIS(0): Not using default mode "1024x768" (vrefresh out of range)
(II) SIS(0): Not using default mode "1024x768" (vrefresh out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1024x768" (hsync out of range)
(II) SIS(0): Not using default mode "1280x1024" (unknown reason)
(II) SIS(0): Not using default mode "1280x1024" (unknown reason)
(II) SIS(0): Not using default mode "1280x1024" (unknown reason)
(II) SIS(0): Not using default mode "1280x1024" (unknown reason)
(II) SIS(0): Not using default mode "1600x1200" (unknown reason)
(II) SIS(0): Not using default mode "1600x1200" (unknown reason)
(II) SIS(0): Not using default mode "1600x1200" (unknown reason)
(II) SIS(0): Not using default mode "1600x1200" (unknown reason)
(II) SIS(0): Not using default mode "1600x1200" (unknown reason)
(II) SIS(0): Not using default mode "1600x1200" (unknown reason)
(II) SIS(0): Not using default mode "1600x1200" (unknown reason)
(II) SIS(0): Not using default mode "1920x1440" (unknown reason)
(II) SIS(0): Not using default mode "1920x1440" (unknown reason)
(II) SIS(0): Not using default mode "1920x1440" (unknown reason)
(II) SIS(0): Not using default mode "1920x1440" (unknown reason)
(II) SIS(0): Not using default mode "1920x1440" (unknown reason)
(II) SIS(0): Not using default mode "1920x1440" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "2048x1536" (unknown reason)
(II) SIS(0): Not using default mode "2048x1536" (unknown reason)
(II) SIS(0): Not using default mode "2048x1536" (unknown reason)
(II) SIS(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "2048x1536" (bad mode clock/interlace/doublescan)
(II) SIS(0): Not using default mode "1280x800" (vrefresh out of range)
(II) SIS(0): Not using default mode "1280x800" (hsync out of range)
(--) SIS(0): Virtual size is 1280x800 (pitch 1280)
(**) SIS(0): *Default mode "1280x800" (1280x800) (For CRT device: 107.9 MHz, 63.9 kHz, 59.9 Hz)
(**) SIS(0):  Default mode "1024x768" (1024x768) (For CRT device: 65.1 MHz, 48.5 kHz, 60.1 Hz)
(**) SIS(0):  Default mode "800x600" (800x600) (For CRT device: 40.0 MHz, 37.9 kHz, 60.3 Hz)
(**) SIS(0):  Default mode "640x480" (640x480) (For CRT device: 25.1 MHz, 31.3 kHz, 59.7 Hz)
(==) SIS(0): DPI set to (100, 100)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib64/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "xaa"
(II) LoadModule: "xaa"
(II) Loading /usr/lib64/xorg/modules//libxaa.so
(II) Module xaa: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.2
(II) SIS(0): 2D acceleration enabled, modename xaa
(II) Loading sub module "dri"
(II) LoadModule: "dri"
(II) Loading /usr/lib64/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) Loading sub module "glx"
(II) LoadModule: "glx"
(II) Loading /usr/lib64/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(==) AIGLX enabled
(II) Loading extension GLX
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xb0000000 - 0xb001ffff (0x20000) MX[B]
	[1] 0	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xb0100000 - 0xb0103fff (0x4000) MX[B]
	[7] -1	0	0xb0307000 - 0xb030707f (0x80) MX[B]
	[8] -1	0	0xb0106000 - 0xb0106fff (0x1000) MX[B]
	[9] -1	0	0xb0105000 - 0xb0105fff (0x1000) MX[B]
	[10] -1	0	0xb0104000 - 0xb0104fff (0x1000) MX[B]
	[11] -1	0	0xa0000000 - 0x9fffffff (0x0) MX[B]O
	[12] -1	0	0xb0000000 - 0xb001ffff (0x20000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprU)
	[15] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprU)
	[16] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprU)
	[17] 0	0	0x00009000 - 0x0000907f (0x80) IX[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x000010a0 - 0x000010af (0x10) IX[B]
	[21] -1	0	0x000010b8 - 0x000010bb (0x4) IX[B]
	[22] -1	0	0x000010c0 - 0x000010c7 (0x8) IX[B]
	[23] -1	0	0x000010bc - 0x000010bf (0x4) IX[B]
	[24] -1	0	0x000010c8 - 0x000010cf (0x8) IX[B]
	[25] -1	0	0x00001000 - 0x0000107f (0x80) IX[B]
	[26] -1	0	0x00001080 - 0x0000108f (0x10) IX[B]
	[27] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[28] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[29] -1	0	0x000001f0 - 0x000001f0 (0x1) IX[B]
	[30] -1	0	0x000001f0 - 0x000001f7 (0x8) IX[B]
	[31] -1	0	0x00009000 - 0x0000907f (0x80) IX[B](B)
	[32] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[33] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) Loading sub module "vbe"
(II) LoadModule: "vbe"
(II) Loading /usr/lib64/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.1.0
	ABI class: X.Org Video Driver, version 1.2
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Loading /usr/lib64/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.2
(II) SIS(0): initializing int10
(II) SIS(0): Primary V_BIOS segment is: 0xc000
(II) SIS(0): VESA BIOS detected
(II) SIS(0): VESA VBE Version 3.0
(II) SIS(0): VESA VBE Total Mem: 131072 kB
(II) SIS(0): VESA VBE OEM: SiS
(II) SIS(0): VESA VBE OEM Software Rev: 1.0
(II) SIS(0): VESA VBE OEM Vendor: Silicon Integrated Systems Corp.
(II) SIS(0): VESA VBE OEM Product: 6330
(II) SIS(0): VESA VBE OEM Product Rev: 3.72.02
(==) SIS(0): Write-combining range (0xc0000000,0x8000000)
(II) SIS(0): Setting standard mode 0x16
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: open result is -1, (No such device or address)
drmOpenDevice: Open failed
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 8, (OK)
drmOpenByBusid: drmOpenMinor returns 8
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(II) [drm] loaded kernel module for "sis" driver.
(II) [drm] DRM interface version 1.3
(II) [drm] DRM open master succeeded.
(II) SIS(0): [drm] Using the DRM lock SAREA also for drawables.
(II) SIS(0): [drm] framebuffer handle = 0xc0000000
(II) SIS(0): [drm] added 1 reserved context for kernel
(II) SIS(0): X context handle = 0x1
(II) SIS(0): [drm] installed DRM signal handler
(II) SIS(0): [dri] Video RAM memory heap: 0x1400000 to 0x7f70000 (110016KB)
(II) SIS(0): [dri] handle = 0xb0000000, size = 65536
(II) SIS(0): [drm] AGP enabled
(II) SIS(0): [drm] Allocated 32MB AGP memory
(II) SIS(0): [drm] Bound 32MB AGP memory
(II) SIS(0): [drm] No valid IRQ number for device 1:0:0 (code -22)
(II) SIS(0): [MC] GART: Allocated 7172KB for HWMC
(II) SIS(0): [dri] Visual configs initialized
(II) SIS(0): Framebuffer from (0,0) to (1279,4094)
(II) SIS(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Solid filled rectangles
	8x8 mono pattern filled rectangles
	8x8 color pattern filled rectangles
	Solid Lines
	Dashed Lines
	Offscreen Pixmaps
	Setting up tile and stipple cache:
		32 128x128 slots
		26 256x256 slots
		7 512x512 slots
		32 8x8 color pattern slots
(--) SIS(0): CPU frequency 1733.00Mhz
(II) SIS(0): Benchmarking system RAM to video RAM memory transfer methods:
(--) SIS(0): 	Checked libc memcpy()... 	235.6 MiB/s
(--) SIS(0): 	Checked built-in-1 memcpy()... 	235.8 MiB/s
(--) SIS(0): 	Checked built-in-2 memcpy()... 	235.7 MiB/s
(--) SIS(0): 	Checked SSE memcpy()... 	239.2 MiB/s
(--) SIS(0): Using SSE method for aligned data transfers to video RAM
(--) SIS(0): Using built-in-1 method for unaligned data transfers to video RAM
(==) SIS(0): Backing store disabled
(==) SIS(0): Silken mouse enabled
(**) Option "dpms"
(**) SIS(0): DPMS enabled
(--) SIS(0): Hardware supports one video overlay
(II) SIS(0): Using SiS300/315/330/340/350 series HW Xv by default on CRT2
(II) SIS(0): [MC] This chip does not support XvMC.
(II) SIS(0): Default Xv adaptor is Video Overlay
(II) SIS(0): [DRI] installation complete
(II) SIS(0): Direct rendering enabled
(II) SIS(0): Initialized SISCTRL extension version 0.1
(II) SIS(0): Registered screen 0 with SISCTRL extension version 0.1
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: Searching for BusID pci:0000:01:00.0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 9, (OK)
drmOpenByBusid: drmOpenMinor returns 9
drmOpenByBusid: drmGetBusid reports pci:0000:01:00.0
(EE) AIGLX error: dlopen of /usr/lib64/dri/sis671_dri.so failed (/usr/lib64/dri/sis671_dri.so: cannot open shared object file: No such file or directory)
(EE) AIGLX: reverting to software rendering
(II) Loading sub module "GLcore"
(II) LoadModule: "GLcore"
(II) Loading /usr/lib64/xorg/modules/extensions//libGLcore.so
(II) Module GLcore: vendor="X.Org Foundation"
	compiled for 1.3.0, module version = 1.0.0
	ABI class: X.Org Server Extension, version 0.3
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(**) Option "CoreKeyboard"
(**) Keyboard0: Core Keyboard
(**) Option "Protocol" "standard"
(**) Keyboard0: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Keyboard0: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Keyboard0: XkbModel: "pc105"
(**) Option "XkbLayout" "gb"
(**) Keyboard0: XkbLayout: "gb"
(**) Option "CustomKeycodes" "off"
(**) Keyboard0: CustomKeycodes disabled
(II) Synaptics touchpad driver version 0.14.6 (1406)
(--) Synaptics auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(--) Synaptics touchpad found
(**) Option "CorePointer"
(**) Synaptics: Core Pointer
(WW) <default pointer>: No Device specified, looking for one...
(II) <default pointer>: Setting Device option to "/dev/input/mice"
(--) <default pointer>: Device: "/dev/input/mice"
(==) <default pointer>: Protocol: "Auto"
(**) Option "AlwaysCore"
(**) <default pointer>: always reports core events
(==) <default pointer>: Emulate3Buttons, Emulate3Timeout: 50
(**) <default pointer>: ZAxisMapping: buttons 4 and 5
(**) <default pointer>: Buttons: 9
(**) <default pointer>: Sensitivity: 1
(II) XINPUT: Adding extended input device "<default pointer>" (type: MOUSE)
(II) XINPUT: Adding extended input device "Synaptics" (type: MOUSE)
(II) XINPUT: Adding extended input device "Keyboard0" (type: KEYBOARD)
Synaptics DeviceInit called
SynapticsCtrl called.
Synaptics DeviceOn called
(--) Synaptics auto-dev sets device to /dev/input/event2
(**) Option "Device" "/dev/input/event2"
(--) Synaptics touchpad found
(II) <default pointer>: Setting mouse protocol to "ExplorerPS/2"
(II) <default pointer>: ps2EnableDataReporting: succeeded
SynapticsCtrl called.
---------------------------------------------------

Many thanks.

---

### Post by ahmedkom on 2008-06-26
Whta is the difference between the 2D and 3D treiber inside the treiber? , I think they are the same but we have to change somthing inside the treiber to make a 3D or to use the 3D abilities of the treiber.

on other hand i think we can use some pressure on SIS to get the treiber throw mailing them everyday to ask them for it .

---

### Post by debianite on 2008-06-26
> **ahmedkom said:**
> 
on other hand i think we can use some pressure on SIS to get the treiber throw mailing them everyday to ask them for it .

I'll be happy to, can you please share the sis email with us?

---

### Post by ahmedkom on 2008-06-26
> **ahmedkom said:**
> Whta is the difference between the 2D and 3D treiber inside the treiber? , I think they are the same but we have to change somthing inside the treiber to make a 3D or to use the 3D abilities of the treiber.

on other hand i think we can use some pressure on SIS to get the treiber throw mailing them everyday to ask them for it .

as I emailed SIS for the Driver i got an email with link to the SIS downloads so helpful were they so. I think when every one of us sends every day an email requesting the same driver they must obay our request so give it a try.

---

### Post by debianite on 2008-06-26
> **ahmedkom said:**
> as I emailed SIS for the Driver i got an email with link to the SIS downloads so helpful were they so. I think when every one of us sends every day an email requesting the same driver they must obay our request so give it a try.

What i meant was the actual email address from sis it self, as i cant find than any were on their website.

---

### Post by tarekragabmabrouk on 2008-06-26
> **debianite said:**
> What i meant was the actual email address from sis it self, as i cant find than any were on their website.

ya i have the same problem 
if any one knows their email pls tell me

---

### Post by ahmedkom on 2008-06-29
To contact SIS follow this link

[http://www.sis.com/MailContact/MailContactNew.php?CSN=6](http://www.sis.com/MailContact/MailContactNew.php?CSN=6)

---

### Post by Father D on 2008-06-30
> **ahmedkom said:**
> To contact SIS follow this link

[http://www.sis.com/MailContact/MailContactNew.php?CSN=6](http://www.sis.com/MailContact/MailContactNew.php?CSN=6)

Many thanks ahmedkom ... mail has gone off to them already ... lets inundate them!!:lolflag:

---

### Post by v4mpiro on 2008-06-30
hi all! i also wrote to them. i hope this will make them release their drivers!!!

---

### Post by drahmin on 2008-07-05
Hello everyone.I've installed ubuntu 8.04 to my computer at work, and when i tried to activate compiz i realized that my work computer has sis graphic card on it :(
i've installed 2d allready and everything is working fine.Ubuntu is still perfect for me without special effects but believe me i really need some of those tricks while working with a lot of stuff :)
I've read the whole post and i guess still no 3d driver right?

---

### Post by Claus_ on 2008-07-07
> **drahmin said:**
> Hello everyone.I've installed ubuntu 8.04 to my computer at work, and when i tried to activate compiz i realized that my work computer has sis graphic card on it :(
i've installed 2d allready and everything is working fine.Ubuntu is still perfect for me without special effects but believe me i really need some of those tricks while working with a lot of stuff :)
I've read the whole post and i guess still no 3d driver right?

Still no 3D driver indeed. 
You can run Compiz anyway but the performance is very poor. I mean very. And the cores jump from 2-4% each to 35-45 %.

---

### Post by drahmin on 2008-07-07
Dear Claus_
It's so sad that still no 3d :(
But can you please explain me how to get compiz working without 3d? :confused:

I do not have any restricted drivers in my list and when i try to activate special effects, it says special effects could not be activated. :(

---

### Post by Claus_ on 2008-07-07
> **drahmin said:**
> Dear Claus_
It's so sad that still no 3d :(
But can you please explain me how to get compiz working without 3d? :confused:

I do not have any restricted drivers in my list and when i try to activate special effects, it says special effects could not be activated. :(

I'm not at my Linux PC right now but...
Try this:
1- Add to your Xorg.conf in Device:
```
Option "AddARGBGLXVisuals" "True"
```

2- Install and run Compiz Check. Look at ->  [http://forlong.blogage.de/article/pages/Compiz-Check]("http://forlong.blogage.de/article/pages/Compiz-Check")
You'll be prompted to skip Compiz white list check, say "yes"

3- Install "xserver-xgl" from synaptic.

4- Write Compiz in a terminal.

Let me know your results, but my GLXGEARS drop from -already poor- 350 to 120 with Normal effects and to 75 with Extras.
Good luck

---

### Post by Jerzabek39 on 2008-07-07
It doesnt work for me, i cant still have compiz.. :(

EDIT: I am stupid, it works but you are right, very VERY slow :D

---

### Post by Claus_ on 2008-07-07
> **Jerzabek39 said:**
> It doesnt work for me, i cant still have compiz.. :(

EDIT: I am stupid, it works but you are right, very VERY slow :D

I think that's kind of good news, because Compiz it's expected to work ok with SiS cards ones the 3d driver be released -if that happens some day-:(

---

### Post by debianite on 2008-07-08
I just left SIS a message in the link provided earlier.
I strongly suggest the all do the same and try to put some pressure on them.

---

### Post by Creap on 2008-07-10
After reading this thread through, I went to Dennis' great Wiki (thanks!). Reading there, I decided to try simply editing my xorg.conf, keeping the VESA drivers since my laptop is mainly a IRC/web machine, where I won't need any heavy graphics. 

However, my monitor is a 15.4" WXGA (1280x800). No matter what resolutions I enter to my xorg.conf my max resolution stays at 1280x768. 1280x720 doesn't work either. Needless to say, a normal resolution on my widescreen monitor looks crap. Do you think it would be worthwhile to try the SiS drivers? It's a SiS 771/671 which would make it Otto D's modified drivers, right?

Thanks.

---

### Post by Claus_ on 2008-07-10
> **Creap said:**
> After reading this thread through, I went to Dennis' great Wiki (thanks!). Reading there, I decided to try simply editing my xorg.conf, keeping the VESA drivers since my laptop is mainly a IRC/web machine, where I won't need any heavy graphics. 

However, my monitor is a 15.4" WXGA (1280x800). No matter what resolutions I enter to my xorg.conf my max resolution stays at 1280x768. 1280x720 doesn't work either. Needless to say, a normal resolution on my widescreen monitor looks crap. Do you think it would be worthwhile to try the SiS drivers? It's a SiS 771/671 which would make it Otto D's modified drivers, right?

Thanks.

Try to install the 2d drivers and/or edit your xorg.conf to include that resolution in "Monitor" as in "Screen", specialy the Virtual parameter:

```

.
.
.
Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Generic LCD Display"
	Modelname	"LCD Panel 1280x800"
	Horizsync	31.5-50.0
	Vertrefresh	56.0 - 65.0
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1280	800
		Modes		"1280x768@60"	"1280x720@60"	"800x600@60"	"1280x800@60"	"800x600@56"
	EndSubSection
EndSection
.
.
.

```

---

### Post by Father D on 2008-07-11
> **Claus_ said:**
> Try to install the 2d drivers and/or edit your xorg.conf to include that resolution in "Monitor" as in "Screen", specially the Virtual parameter:



Thanks Claus_ I gave this a try with the Vesa driver (I have given up with the Sis driver for the moment, the Mandriva 64bit does not play nicely with certain GTK+ windows! on my Fedora 8 _64)
Only problem is; as you will know the Vesa driver does not include a 1280x800 mode, instead it simply uses 1280x768, this results in faint banding across the screen .. nasty!

Setting the 'virtual' parameter in xorg.conf looked like a promising idea ... BUT! The vesa driver obviously misreads the screen size without the 'virtual' parameter .. so therefore stretches beyond the screen edge when the 'virtual' parameter is set to 1280x800, worst of all the banding remains :frown:

Many thanks for the tip though .. any other ideas? .. anyone? I just want a clean 1280x800!

---

### Post by Jerzabek39 on 2008-07-11
Is it possible that this "new" drivers dont work for 8.10? :confused:

---

### Post by drahmin on 2008-07-12
Done everything, restarted x and viola i can use special effects now.Thanks!

But it's..Really...Slow :D

I think i will beg to sis for a 3d driver :(

---

### Post by woodpeaker on 2008-07-17
sent request to the SIS for the drivers for the Linux.. but they still didn't answer me....

hope Spam bot helps me))

---

### Post by SinglePack on 2008-07-17
FSC as the vendor of my Notebook told me, they only support windows.

Yeeha!

Unbelievable.


:?

---

### Post by woodpeaker on 2008-07-18
That's why I don't understand why they sell laptop without OS... and with preinstalled Linux

---

### Post by Creap on 2008-07-20
Zepto claimed they haven't found any drivers themselves.

---

### Post by beny-4.56 on 2008-07-21
i need the 64bit one. can help me?:-k

---

