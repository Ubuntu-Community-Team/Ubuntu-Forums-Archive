---
title: "rx 480 driver problem."
date: 2016-11-22
forum: Hardware
---

### Post by kristiaandejong on 2016-11-22
I got a problem with the amd drivers on Uuntu 16.10. The amd driver dont seem to work, and the offical driver from amd has may mistakes in the install file ( according by a friend who lookt at it).

I have now the mesa drivers who can see that i got a Polaris gpu, and it works with steam and very laggy in wine depend on the game. 

Here my problem, Ubuntu doest see the the rx480 driver, and I have a lot of problem with it.  Example with Lightworks ( im a sony vegas editor but i cant get that to work on my pc too ), 
but I cant get it to work bc(probly) he doesnt see the amdgpu driver. ( lookt it up online).
I am looking for days to fix this, maybe I dont see it, or cant handle good with not enough infomation ( im a beginner in ubuntu/linux ).
If some one would help me with the drivers, it would be awsome!

Thanks!

---

### Post by QIII on 2016-11-22
Hello!

What do you mean by "doesn't seem to work".  What do you mean by "official driver"?  What expertise does your friend bring to bear?

After my testing, I can assure you with great confidence that both AMDGPU and AMDGPU-PRO work well with the GCN 1.2 and newer cards.  According to AMD, some GCN 1.1 cards are now supported. [ Phoronix.com]("http://www.phoronix.com/scan.php?page=article&item=amdgpu-rx480-linux&num=1") has been testing and evaluating AMDGPU and AMDGPU-PRO for many months.  According to them those drivers work.

If your desired software does not work with AMDGPU, there is little we or AMD can do about that until the software is rewritten.

---

### Post by kristiaandejong on 2016-11-22
> **QIII said:**
> Hello!

What do you mean by "doesn't seem to work".  What do you mean by "official driver"?  What expertise does your friend bring to bear?

After my testing, I can assure you with great confidence that both AMDGPU and AMDGPU-PRO work well with the GCN 1.2 and newer cards.  According to AMD, some GCN 1.1 cards are now supported. [ Phoronix.com]("http://www.phoronix.com/scan.php?page=article&item=amdgpu-rx480-linux&num=1") has been testing and evaluating AMDGPU and AMDGPU-PRO for many months.  According to them those drivers work.

If your desired software does not work with AMDGPU, there is little we or AMD can do about that until the software is rewritten.

My has studied at developer and software, and has Ubuntu as os, he knows a lot, but he is a buzzy man.  
My pc doesnt see the gpu, other then the unofficial drivers. 
The official driver install from amd, had many typos and mistakes in the install script according my friend, so the official driver wouldn't install basically.
It should work, the rx480 is a supported driver for Ubuntu.

---

### Post by QIII on 2016-11-22
What do you mean by the "unofficial" driver?  What do yo mean by the "official" driver?  What- exactly - happens when you try to install drivers?

Apparently phoronix.com and I have been able to install AMDGPU and AMDGPU-PRO without problems.  I run 16.10 with it, so I am curious what problems your friend has found with it.

We still do not know what the exact nature of your issues with the driver are.  We can't begin to help without that information.

---

### Post by kristiaandejong on 2016-11-22
> **QIII said:**
> What do you mean by the "unofficial" driver?  What do yo mean by the "official" driver?  What- exactly - happens when you try to install drivers?

Apparently phoronix.com and I have been able to install AMDGPU and AMDGPU-PRO without problems.  I run 16.10 with it, so I am curious what problems your friend has found with it.

We still do not know what the exact nature of your issues with the driver are.  We can't begin to help without that information.

We send this to the amd support 2 weeks ago, maybe this will make it clear: 

Dear amd,   I recently bought an RX480 graphics card, and I'm having quite some trouble getting it to work on the latest ubuntu release. (16.10) I asked a friend of mine, who is professional software engineer and specializes in embedded linux, to take a look. at first he tried to install the AMD-GPUPRO drivers this failed at first because the script tried to create the file /etc/aptsources.list.d/amd-gpupro.list which should be "/etc/apt/sources.list.d/amd-gpupro.list", then the module failed installing with some weird error that some function had too many arguments or something. anyhow I don't know anything about this, eventually my friend installed mesa 13, and while it works it doesn't have the best performance.   Can you please help me out getting the best out of my graphics card?

---

### Post by QIII on 2016-11-22
That is still hardly helpful.  "Something something something error" means nothing.  It won't mean anything to AMD either.

I have not encountered the directory error, but I will research that.

Please provide the exact error messages.  Help us help you.  We don't have crystal balls to magically see what you are seeing.

---

### Post by kristiaandejong on 2016-11-22
> **QIII said:**
> That is still hardly helpful.  "Something something something error" means nothing.  It won't mean anything to AMD either.

I have not encountered the directory error, but I will research that.

Please provide the exact error messages.  Help us help you.  We don't have crystal balls to magically see what you are seeing.

Yes I unsterstand, I kinda have a hard time explaining it correctly. Sorry for that!

But i try to recreate the progress and this is what came out: /Downloads/amdgpu-pro-16.40-348864$ sudo ./amdgpu-pro-install
[sudo] password for xxxxxxx: 
tee: /etc/aptsources.list.d/amdgpu-pro.list: No such file or directory
deb [ trusted=yes ] file:/var/opt/amdgpu-pro-local/ ./

( I did what amd install guide on there site told me to do. ) : [http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx](http://support.amd.com/en-us/kb-articles/Pages/AMDGPU-PRO-Install.aspx)

---

### Post by kristiaandejong on 2016-11-26
Do you know what I can do?

---

### Post by singletrack on 2016-11-26
I am having the same problem after i extracted from downloads (also tried extracting to the tmp directory) then while im in that directory ( tmp/amdgpu-pro-16.40-348864 ) in terminal i type "amdgpu-pro-driver/amdgpu-pro-install" and it says no such file or directory
Is this the correct way to run the script?

And im using ubuntu 16.04

---

### Post by kristiaandejong on 2016-11-27
Afther i edit 
echo ${dir}${etc}${sourceparts}/amdgpu-pro.list
 with
 echo ${dir}${etc}/${sourceparts}/amdgpu-pro.list

I still get this problem, and i just cant fix the scrips :(.

sudo ./amdgpu-pro-16.40-348864/amdgpu-pro-install
./amdgpu-pro-16.40-348864/amdgpu-pro-install: 1: ./amdgpu-pro-16.40-348864/amdgpu-pro-install: &#65279;#!/bin/bash: not found
./amdgpu-pro-16.40-348864/amdgpu-pro-install: 40: ./amdgpu-pro-16.40-348864/amdgpu-pro-install: Syntax error: "(" unexpected

If you want to check this is my current scrips: file:///home/kristaan/Downloads/amdgpu-pro-16.40-348864/amdgpu-pro-install 

I hope you can help me fix the scrips/driver install. :)

---

### Post by QIII on 2016-11-27
Threads merged.

This is, in part, what I was asking for several days ago.

Unfortunately, we cannot look at the script as you have modified it on your machine.

---

