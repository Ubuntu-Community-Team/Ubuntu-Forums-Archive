---
title: "Install XP and remove Ubuntu 7.10?"
date: 2007-10-26
forum: Hardware &amp; Laptops
---

### Post by AZRoboto on 2007-10-26
How can I do that?

I have an XP install disk.  Whenever I put that in, hit "Repair", hit "Enter," it says my computer doesn't have any Hard Drives installed (obviously I do...it's just connected to Ubuntu).

Any solutions or ideas on how to format my hard drive or install XP would be great.  I'm running out of ideas and just want a computer that I am familiar with and has an interface I'm used to.

Please, I really need help.

---

### Post by ilkkal on 2007-10-26
I think the repair is for repairing broken Windows XP system. So obiviosly it's looking for existing Windows XP system. I don't know how to format your hard drive with XP CD, but I think it's possible. Maybe you should post your post to some Windows forum?

---

### Post by jrharvey on 2007-10-26
#1 it says that because repair is for an existing install of windows. If you do not have windows, it cannot repair it. 

#2 you have to reformat the drive to remove ubuntu. Its been a while since i installed windows xp but I think you select "setup windows xp" not "repair"

#3 why would you ever want to ditch ubuntu for XP. If you really want to its up to you but windows is not the best OS to be surfing the web and stuff of that nature. I can't tell you how many times I wanted to throw my computer out the window when I was running XP doe to some stupid spyware and virus.

---

### Post by AZRoboto on 2007-10-26
jrharvey,
#2: idk how to reformat the drive.  And I hit "setup windows xp" but I still get the "no HDD" notification

#3: I've had ubuntu for less than a day, but I'm already not liking how I can't view all my flash videos, or how I have to dig to find iPod support, or how some text loads online, or how I can't hit backspace to go back a page on Firefox.

---

### Post by mikewhatever on 2007-10-26
It looks like you have never installed XP before. Follow this guide [http://www.theeldergeek.com/xp_pro_install_-_graphic.htm](http://www.theeldergeek.com/xp_pro_install_-_graphic.htm)

---

### Post by jrharvey on 2007-10-26
Just to be fair, ubuntu can use flash. Its just that you have to install it.
That is really weird that it tells you that you dont have an HDD. I think you may have a hardware issue. My older computer had an issue simillar to this. I always got the error "can't write to disk" I am pretty sure it was the HDD but I never found out because I got rid of it for a new one.

---

### Post by raptor_computer_systems on 2007-11-01
Is the error no HDD, or no valid partions found?




if no hdd try loading the driver for your HDD controller from windows text based setup.

---

### Post by nikko_bosatsu on 2007-11-01
Maybe XP can't recognize your HD, you need 3rd party driver. You can boot to Ubuntu ? if you can, then find 3rd party driver for your HD, btw to install Flash at Ubuntu so easy just as 123 ( except if you do not have internet connection).

---

### Post by sistoviejo on 2007-11-01
Maybe you have to load the sata driver for your hard drive when you boot into the windows installation CD. You should try to find out what model/brand HD you have.
Then you can check the website of manufacturer to download drivers for XP.

Setting backspace to go back in firefox is easy:
Type about:config on the address bar and hit enter.
Then you have to find a key which is called browser.backspace_action and set it to 0.

After trying to see a video on youtube I noticed I didn't have flash plugin installed.
It was really easy to install. I only had to go to system>administration>synaptic package manager
Then I searched for flashplugin-nonfree and install it.
Afterwards I was able to see youtube videos no problem.

Here's another idea: You could install a virtual machine with Windows XP!
That will probably give you no HDD problems.

---

### Post by bastonal on 2008-01-25
> **jrharvey said:**
> #1 it says that because repair is for an existing install of windows. If you do not have windows, it cannot repair it. 

#2 you have to reformat the drive to remove ubuntu. Its been a while since i installed windows xp but I think you select "setup windows xp" not "repair"

#3 why would you ever want to ditch ubuntu for XP. If you really want to its up to you but windows is not the best OS to be surfing the web and stuff of that nature. I can't tell you how many times I wanted to throw my computer out the window when I was running XP doe to some stupid spyware and virus.
  

Doesn't it bother you that one has to do a song and a dance to put ANYTHING on Ubuntu such as real Audio media Player,...and if you do for so many there are bugs or a pale immitation or your forced to buy VLC player... Yeah windows XP sucks....but Now I can't burn my coded movies with one-click software, I'm sure there's not one for coded movies in Ubuntu my mp3 software is for windows etc..my mouse buttons aren't reconised, again a song & dance to an unfamiliar OS to even attempt to try and get ti to work some of my hardware isn't reconized....s
Seriously besides all that Ubuntu runs smooth and is fast and I like so much about it...but I'm think I'm going back to XP sp2.

---

### Post by mrojas73 on 2008-01-25
> **bastonal said:**
> Doesn't it bother you that one has to do a song and a dance to put ANYTHING on Ubuntu such as real Audio media Player,...and if you do for so many there are bugs or a pale immitation or your forced to buy VLC player... Yeah windows XP sucks....but Now I can't burn my coded movies with one-click software, I'm sure there's not one for coded movies in Ubuntu my mp3 software is for windows etc..my mouse buttons aren't reconised, again a song & dance to an unfamiliar OS to even attempt to try and get ti to work some of my hardware isn't reconized....s
Seriously besides all that Ubuntu runs smooth and is fast and I like so much about it...but I'm think I'm going back to XP sp2.

Linux is not for every one, specially for those who don't understand computers,

---

### Post by OmegaBLK on 2008-01-25
> **bastonal said:**
> Doesn't it bother you that one has to do a song and a dance to put ANYTHING on Ubuntu such as real Audio media Player,


One would think not having to install Real Audio Player would be a good thing...

> 
...and if you do for so many there are bugs or a pale immitation or your forced to buy VLC player...


VLC is free (as in beer).  Bugs exist in pretty much every desktop OS.  Not sure what you mean by "pale immitation" so it is best to not respond to that.

> 
 Yeah windows XP sucks....but Now I can't burn my coded movies with one-click software, I'm sure there's not one for coded movies in Ubuntu my mp3 software is for windows etc..


What do you mean by "coded" movies?  Are you referring to DRM?  Encoding?  There are tools to encode/decode and there are applications to burn movies to dvd.  Ubuntu (or FOSS/Linux in general) also has software that can play mp3s.

> 
my mouse buttons aren't reconised,


Have you asked anyone on this forum for help yet?

> 
 again a song & dance to an unfamiliar OS to even attempt to try and get ti to work some of my hardware isn't reconized....s


Did you check to make sure that your hardware was supported before installing Ubuntu?  Did you seek help in these forums or elsewhere to help assist you?

> 
Seriously besides all that Ubuntu runs smooth and is fast and I like so much about it...but I'm think I'm going back to XP sp2.

Sorry to hear that.  If you would ask people on these forums and even the IRC chat-room for help with your problems, I'm sure that they could get them resolved.  **People cannont help you if you do not ask for assistance**.

---

### Post by sistoviejo on 2008-01-26
> **bastonal said:**
> Doesn't it bother you that one has to do a song and a dance to put ANYTHING on Ubuntu such as real Audio media Player,.
I have never liked Real player. I much rather prefer the mp3 format.
Besides I always found it complicated to install in Windows. You have to look for the damn thing on the Internet. Then you have to download it. And finally you would have to install it and hope it works. 
I have never tried in Ubuntu though because as I said... I don't like it.
> **bastonal said:**
> ..and if you do for so many there are bugs or a pale immitation
I searched real player linux and the first result was the original real player for linux made by Real. So you can use the original real player on Linux.
> **bastonal said:**
>  or your forced to buy VLC player... 
You don't have buy VLC player!! It's free and open source. You can download and use it for free. 
> **bastonal said:**
> Yeah windows XP sucks...
Does it really? I do prefer Vista right now. I have a Ubuntu and Windows Vista. But I don't think XP sucks.
> **bastonal said:**
> 
.but Now I can't burn my coded movies with one-click software, 
I'm sure there's not one for coded movies in Ubuntu 

I don't encode movies so I can't answer this.
> **bastonal said:**
> my mp3 software is for windows 

I also found that Linux lacks a nice mp3 player. Songbird looks quite nice but it is still beta.
I really like Amarok. You should try it. But my player of choice has always been Winamp. 
> **bastonal said:**
> 
etc..my mouse buttons aren't reconised, 

This never happened to me. What mouse do you have?
> **bastonal said:**
> 
again a song & dance to an unfamiliar OS to even attempt to try and get ti to work some of my hardware isn't reconized....s

Exactly what hardware isn't recognized? 
There's a lot of hardware that is recognized... So you can't just claim that hardware isn't recognized. Be specific.
> **bastonal said:**
> 
Seriously besides all that Ubuntu runs smooth and is fast and I like so much about it...but I'm think I'm going back to XP sp2.
just out of curiosity... For how long did you try with Ubuntu? 

Hope you can also find what you're looking for in Ubuntu. 
Cheers. :)

---

### Post by bastonal on 2008-01-26
> **sistoviejo said:**
> I have never liked Real player. I much rather prefer the mp3 format.
Besides I always found it complicated to install in Windows. You have to look for the damn thing on the Internet. Then you have to download it. And finally you would have to install it and hope it works. 
I have never tried in Ubuntu though because as I said... I don't like it.

I searched real player linux and the first result was the original real player for linux made by Real. So you can use the original real player on Linux.

You don't have buy VLC player!! It's free and open source. You can download and use it for free. 

Does it really? I do prefer Vista right now. I have a Ubuntu and Windows Vista. But I don't think XP sucks.

I don't encode movies so I can't answer this.

 

I also found that Linux lacks a nice mp3 player. Songbird looks quite nice but it is still beta.
I really like Amarok. You should try it. But my player of choice has always been Winamp. 

This never happened to me. What mouse do you have?

Exactly what hardware isn't recognized? 
There's a lot of hardware that is recognized... So you can't just claim that hardware isn't recognized. Be specific.

just out of curiosity... For how long did you try with Ubuntu? 

Hope you can also find what you're looking for in Ubuntu. 
Cheers. :)

Thanks for your kind & understanding post....

I had Ubuntu installed for about three days now...

However,  I can't even make anything stay pasted in Terminal...I go to Accessories, click on "Terminal" paste a line I was told to and click off Terminal and back on and the line(es) I pasted are always gone....So I can't even figure that out so I'll never get codes to stick in Terminal....Well I'm lost....that's why I said I wanted to go back to XP because I know every file, .dll etc. backwards and forward, there's nothing I can't figure out on XP....but it's so clunky compared to Ubuntu...I Just wish I knew my way around better..

Thanks and Cheers!

---

### Post by sistoviejo on 2008-01-27
Ubuntu is very different to Windows.
It's probably really hard to learn Ubuntu once you have learned to do everything on Windows.

---

### Post by shutslar on 2008-01-27
> I had Ubuntu installed for about three days now...

However, I can't even make anything stay pasted in Terminal...I go to Accessories, click on "Terminal" paste a line I was told to and click off Terminal and back on and the line(es) I pasted are always gone....So I can't even figure that out so I'll never get codes to stick in Terminal....Well I'm lost....that's why I said I wanted to go back to XP because I know every file, .dll etc. backwards and forward, there's nothing I can't figure out on XP....but it's so clunky compared to Ubuntu...I Just wish I knew my way around better..

I don't want to sound like I am ragging on you.  That is not my intent.  What I would like to do is ask you to give Ubuntu a little more time than 3 days.  Please try to remember back to your first 3 days of Windows.  Did you know after those first 3 days what you know now?  

I think you will find that if you use the community that is available to you here and elsewhere on the net you will learn as much about Ubuntu as you already know about Windows and in a much shorter time (because the FOSS community has a passion for helping people).  

Dual boot, use both worlds until you get more comfortable.  It will be worth your effort.

Best Regards

---

### Post by AndyC_772 on 2008-01-27
> **AZRoboto said:**
> How can I do that?

I have an XP install disk.  Whenever I put that in, hit "Repair", hit "Enter," it says my computer doesn't have any Hard Drives installed (obviously I do...it's just connected to Ubuntu).

Any solutions or ideas on how to format my hard drive or install XP would be great.  I'm running out of ideas and just want a computer that I am familiar with and has an interface I'm used to.

Please, I really need help.

I'd echo some of the comments above, Ubuntu is quite different to Windows and I'd agree that a lot of the things that should 'just work' out of the box, don't. But that's not to say that they can't be done, you just need to install the right software. Just like you did in Windows.

If you really want to install XP, the problem is probably that your hard disc is a SATA drive, as in most PCs for the last couple of years. IIRC, when you boot from the XP disc, an option briefly comes up along the lines of 'press F6 to install a third party SCSI or RAID driver', and that's what you need to do. You just need to get the driver first, and for that you'll need to know exactly what hardware you have.

What's the make / model of your motherboard or notebook?

On my PC there's also an option in the BIOS setup to switch the hard disc interface between 'enhanced' and 'compatibility' modes. Put it in 'compatibility' mode and the XP disc will see your hard drive straight away. (Disclaimer: tinkering in BIOS settings can break your PC, so don't change anything you don't understand - and whatever you do, don't blame me for the consequences!)

That said, if there are specific things you want to do in Ubuntu but can't, it's worth asking about them specifically. Get to know Synaptic Package Manager (on the System > Administration menu), it's your gateway to a huge amount of completely free software - something which came as a bit of a shock to my system initially as there's nothing like it in the Windows environment.

---

### Post by jocko on 2008-01-27
> **bastonal said:**
> However,  I can't even make anything stay pasted in Terminal...I go to Accessories, click on "Terminal" paste a line I was told to and click off Terminal and back on and the line(es) I pasted are always gone....So I can't even figure that out so I'll never get codes to stick in Terminal....

Stay pasted in terminal? In the terminal you should **run** the commands, i.e hit enter after you have typed or pasted them there, otherwise they won't do anything.

---

