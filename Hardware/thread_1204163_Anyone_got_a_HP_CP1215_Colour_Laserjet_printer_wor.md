---
title: "Anyone got a HP CP1215 Colour Laserjet printer working?"
date: 2009-07-04
forum: Hardware
---

### Post by Bucky Ball on 2009-07-04
* **This is now solved**. If you are using 8.04 and *having problems* with *HP CP1215 colour laserjet printe*r, you need to install the latest HPLip to fix. [B]See last post for instructions.
[/B]

Hi all,

Just wondering if anyone has managed to get a HP colour laserjet printer model CP1215 working in Ubuntu 8.04?

A friend has been having problems getting one to work for months now and I am heading over their way in about a week so want to start getting some ideas now in the hopes of fixing that up.

I have some ideas but the more the merrier. We have tried plenty attempting to fix it over the phone and online so I must admit I don't have too many ideas left. Distance has been a problem and I may just be able to fix it when I am actually sitting in front of the machine as the OP is new to Ubuntu and a things get lost in translation trying to explain from 750kms away.

Anyhow, all ideas gratefully accepted and if you have successfully installed one of these machines using hp-lip (the latest version is required I believe) and hp-setup, how did you do it? We can't seem to find hp-setup nor install it, which is the bit that loads the driver for this particular printer (they are not included in the hp-lip package, hp-setup installs separately).

Strange thing is, I built the machine here, set it up so all was working fine but don't remember exactly how I got the printer up, but hopefully I can figure that out again. Is was picked up from here and set up OP's end and the printer's not working. Hmm. It shows and is recognised, just won't print which suggests the absence of the drivers installed with hp-setup (as the HP web-site also suggests). :)

---

### Post by Bucky Ball on 2009-07-05
Any takers?

Bump

---

### Post by Bucky Ball on 2009-07-08
bump

---

### Post by RichardCL on 2009-07-17
My CP1215 is just working. It just worked straight out of the box.

My current setup is 9.04 upgraded from 8.10. I also had the CP1215 working on my old laptop that was running Linux2one, based on the 8.04 LTS.

Unfortunately, I didn't do anything other than just plug it in and print so I can't tell you a work around. Do let me know if any other info about my setup would help.

---

### Post by Bucky Ball on 2009-07-17
Done. I am in Melbourne now for about four days and have spent the last day fixing things with that box. 

I installed the latest HPLip from here:

[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

... then followed my nose. For these printers a plugin needs to be loaded which is not part of HPLip. The option is now there to load it when it identifies the printer and realises it needs that plugin. Easy.

The difficulty was really my mother-in-law and I trying to fix things over the phone and internet. She is, for the moment, inexperienced with Ubuntu (nearly 70 and 6 months into Ubuntu after years of MS; more strength to the lady!)  but she did an excellent job and having sat there and done it, I realise we were almost there. 

I downloaded and installed the newest hplip, followed my nose, and had it done in less than ten. Sweet. 8.10 and 9.04 would probably have the newer hplip incidentally, possibly why you have never had any problems. 

Cheers and thanks for the post. :)

---

### Post by Bucky Ball on 2009-07-25
Just tying this up ...

As mentioned, I got over to Melbourne, downloaded the latest HPLip and followed the instructions for installing. When I got to the part to unplug and re-plug the printer, I did so, it was picked up straight away, GUI came up telling me this printer needs a separate plug-in, did I want to install it, I agreed, grind grumble work work work whirr and other machine noises then ... good to go. Printer installed, fantastic printer configuration utility from HP for Linux, test page achieved and all sweet and seemingly rock solid when I left a week later.

* Bottom line if you are having problems with the HP CP1215 Colour Laser Jet printer on Ubuntu Hardy 8.04 (the updated HPLip is included in later versions):

Download the latest HPLip from here:

[http://hplipopensource.com/hplip-web/gethplip.html](http://hplipopensource.com/hplip-web/gethplip.html)

... then follow the instructions here:

[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

Follow your nose from there and you should be good to go. :)

---

### Post by russelld on 2011-01-17
Installing this printer in Linux was an absolutely resounding success!!

Printing in Linux was necessary for me, so I asked the OfficeWorks sales rep (shameless plug ;)) if it would, and they did a quick "google" at the point of sale terminal  and found links to  an open source package in Linux that supports this printer.  

[http://sourceforge.net/projects/hplip/]("http://sourceforge.net/projects/hplip/")

After downloading the package, and decompressing, the "readme" is quite clear, and provides instructions to run the install from the command line. This is straight forward and the application found the distro this machine was running (Ubuntu hardy 8.04b), asked for root access (!). this was  bit spooky and but as nothing was mentioned about this aspect on the net so I let it run.

 It then checked for packaged installed and then requested to download extra packages which were then installed. The installer then proceeded to start compiling the driver which took about 15-20 mins on this 1.3Ghz celeron,.  After it finished compiling, the installer installed the new minted driver and  then gave instructions on how to run the gui admin tool which was unnecessary as the gui admin tool was loaded into the menu and desktop!!

After geting the admin tool running, I plugged in the printer USB, the printer was found straight away, and didn't bother to print a test page, I printed a much needed product labels and invoice straight away!! woot!!:popcorn:
Absolutely incredible, thanks HP and thanks devs! :D

---

### Post by Bucky Ball on 2011-01-18
Better than that you don't need to go to sourceforge to download hplip. It is in the repositories:

System>Admin>Synaptic Package Manager, search for hplip. Even easier. ;)

---

