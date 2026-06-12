---
title: "Help selecting and installing Linux Distro"
date: 2009-09-17
forum: Installation &amp; Upgrades
---

### Post by Pauly BC on 2009-09-17
I need some help in selecting a Linux Distro to best suit my needs. I'm not a hard core programmer and I don't have heaps of time to make every little widget work. I'm here because I have lost faith in Microsoft and I believe Linux must be better.

Has anyone noticed in the last few months as we approach the sales launch of Windows 7 that Vista is slowing down? Our computer is getting geriatric these days...

I tried the major distros off live CD's including Jaunty 32 and 64, OpenSUSE, OpenSolaris and Fedora. Among those distros I found Ubuntu 64 had the fastest boot time and the best 'out of the box' success rate at mounting Windows drives, operating hardware, etc. I also tried Mint and MoonOS, both of which are very nice add-ons to Ubuntu, albeit they use more RAM, slow down the boot time, plus those smaller community distros can lag on updates. I could easily install either of them, but I have doubts and concerns.

I did notice that off the CD, Ubuntu does not play MP3's where both Mint and Moon do. Is that because Jaunty does not include CODECs or is it some other issue? Are the CODECs difficult to install? Can you recommend a better MP3 player than what Ubuntu includes in the CD?

I love the GUI in Moon, I believe if is called Enlightenment, is it difficult to install into Ubuntu?

Should I go ahead with Jaunty 9.04 or wait until late October for Karmic 9.10? Is there a significant step up in performance? Is it difficult to update from Jaunty to Karmic?

Do you need to load in a separate anti-virus program into Linux? I'm running AVG in Vista and it is OK.

Can I load programs from Mint into Ubuntu? Specifically I like their software repository interface, it seemed more user-friendly than what comes with Ubuntu. Similarly can I load enlightenment from Moon into Ubuntu?

In all the distros I tried I noticed the sound was extremely quiet. I have an ASUS P5B motherboard and the built-in surround sound works great for me. Jaunty, Mint and Moon all load it properly but I had to turn on all the speakers through the sound utility, then crank the volume on my speakers to what would be painful in Windows in order to get normal sound. Is there a fix for that?

Can you recommend the most successful way to dual-boot Vista 32 and Ubuntu 64? My wife will still use Vista for her work, bless her heart she is afraid to change. I have a 150 GB partition I released from Windows last night ready to go.

Is there a good email client that can import my MS Outlook 2003 files?

Thanks for your input.

---

### Post by jerrrys on 2009-09-18
here's an answer to mp3

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by rmeske on 2009-09-18
I recently learned about [http://www.osalt.com/](http://www.osalt.com/).  A great site for locating comparable software for linux.  Perhaps you will be able to find a different player there.

In my own experience with two different laptops (4 years old & 10 years old) the players that come with Ubuntu 8.04 Hardy Heron, have worked with just about every media type and the sound level has been great.

---

### Post by jerrrys on 2009-09-18
In my own experience with two different laptops (4 years old & 10 years old) the players that come with Ubuntu 8.04 Hardy Heron, have worked with just about every media type and the sound level has been great.[/quote]

Thats because we are running 8.04...

---

### Post by tonjaa on 2009-09-18
i ever to try like you now i use Ubuntu 9.04 studio because my work need use about graphic and editor video . for me begin learning Linux i use Ubuntu  it's hard bit for new to learning but if you use it for long time
you can understand and use it to easy.  and next time i think Ubuntu can develop for better .
if you want to use in family don't want to try edit more i think Linux Mint7 it's o.k.it's friendly and easy to use.
for 32 and 64 bit i think you can use same if you look at this benchmarks maybe it make you can choose .
[http://http://www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks]("http://http//www.tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks") 
linux for human beings :)

---

### Post by Pauly BC on 2009-09-22
Thanks for the help. I installed Ubuntu 9.04 on my spare partition, no problems. I edited the grub list to make Vista the default boot for my wife, no problems and Windows still operates and does not recognize the presence of Linux at all. Cool!

I downloaded the video driver for my ATI Radeon HD 3850 card and followed the instructions in the help file. The first line of code was successful, the second line gave an error message. Unfortunately the search results I get on forums at home do not match what I get now at work (?!) so I can't recall the commands. Is there a way to remove the drivers, restore Ubuntu's default driver and try again?

The sound driver for my mobo is not working. It is a Realtek 883 system. I downloaded the Linux driver from ASUS and unzipped it, but I do not know how to install it into the system. When I ran Ubuntu off the CD the sound was fine, now it is just static.

I get asked to input my password every 2-3 minutes. Quite obnoxious. Is there a way to make that go away?

Thx

---

### Post by JuergenF on 2009-09-22
> When I ran Ubuntu off the CD the sound was fine, now it is just static.Then the 'driver' is already included, so you don't need to install anything. You'd probably rather bork your system than get it to work ;)
Most no-sound problems are just muted channels. Install the package 'gnome-alsamixer' and unmute interesting sounding channels, and up the volume.

> I get asked to input my password every 2-3 minutes. Quite obnoxious. Is there a way to make that go away?Then you're doing admin-stuff. As soon as you have it all configured to your liking you can run the 'normal' apps without having to reenter your password.

> I downloaded the video driver for my ATI Radeon HD 3850 card and followed the instructions in the help file. The first line of code was successful, the second line gave an error message.Oh missed this one at first.
If you got an error message, you probably haven't installed that 'driver' anyway. In all future cases please show error messages in your post, nobody here knows what's going on otherwise.
And Don't download so much stuff. It's all included - AFAIK there is a proprietary ATI driver in the repositories, so install per your usual package manager or the hardware applet.
You probably should use linux for some weeks before you try to compile additional 3rd-party stuff.

---

### Post by Pauly BC on 2009-09-23
Sorry to complain, but the only advice I am receiving is telling me I should figure this out for myself and I should not use Linux until I know how to use Linux. Thanks for the help.

The sound does not work, the video does not take advantage of the graphics acceleration and the online advice has not helped me.

Right now Vista is running better on my PC than Ubuntu. GASP!

Can anyone with capacity and willingness to help me debug these problems tell me how to give the information required to help get a solution?

---

