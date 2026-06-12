---
title: "Printing issues"
date: 2012-01-02
forum: Hardware
---

### Post by Straemer on 2012-01-02
I recently got a new printer, and have been jumping through hoops trying to get it to work. It's a HP LaserJet Professional M1212nf MFP, and I'm running Ubuntu 11.10 x64. I installed the driver through hplip. After I got it installed, I was getting an insecure filter warning, which I managed to resolve by changing the owner of the filter and backend folders to root. Now whenever I try to print something, the job just gets held. When I try to start it again, it will show its status as being "Processing - Not Connected?" quickly before putting the job back on hold.

I also get the following message from the HP Device Manager whenever I start my computer up:

```
No system tray detected on this system.
Unable to start, exiting.
```

If it helps, the printer is connected to my computer via USB.

Can anyone help me resolve this issue please?

---

### Post by librechick on 2012-01-03
> **Straemer said:**
> I recently got a new printer, and have been jumping through hoops trying to get it to work. It's a HP LaserJet Professional M1212nf MFP, and I'm running Ubuntu 11.10 x64. I installed the driver through hplip. After I got it installed, I was getting an insecure filter warning, which I managed to resolve by changing the owner of the filter and backend folders to root. Now whenever I try to print something, the job just gets held. When I try to start it again, it will show its status as being "Processing - Not Connected?" quickly before putting the job back on hold.

I also get the following message from the HP Device Manager whenever I start my computer up:

```
No system tray detected on this system.
Unable to start, exiting.
```If it helps, the printer is connected to my computer via USB.

Can anyone help me resolve this issue please?

That printer requires a driver plug-in. It isn't one of the better choices for printers form HP. HP though is generally a good bet printer wise. They are the only ones who clearly list which printers are dependent on non-free firmware/plug-ins so you can avoid ones like this. 

That said you shouldn't need to install the driver from HP's web site. The printer requires 3.10.4 and Ubuntu 11.10 has 3.11.7.

You can check out their driver web site at [http://hplipopensource.com/hplip-web/recommended.html](http://hplipopensource.com/hplip-web/recommended.html) for a printer. Verify the plug-in and firmware are not required.

If you want to try and figure out what the problem is try booting from a live cd. See what happens. Maybe there is something screwed up with the installation. Especially now that you have installed a package from HP. That wasn't the wrong move necessarily although doing that can cause problems too (this is true of any device).

---

### Post by Straemer on 2012-01-04
Ok, so I have no idea what I did, but it's somehow working now. It may have been from deleting my .hplip folder (I saw somewhere else that that would remove the message that pops up on startup). Either that or trying to print when it was turned off, cancelling those jobs, and trying to print again after turning it on fixed it.

Thanks for the help anyway librechick.

---

### Post by crazy bird on 2012-01-05
If you encounter some difficulties with your printer, the best to do is upgrading your HPLIP driver first. Best way to do this is manually. The latest HPLIP driver is 3.11.12. Before executing the following below, make sure your **printer is turned off**.
 
What you need to do first is removing all older/previous installed versions of the HPLIP driver to avoid any issues during installation. The "setup wizard" of HPLIP can do this also foru you, but best is to do it yourself before starting the installation of the latest version. This is what you need to do:
 
- open a terminal
- type the following command:
> sudo apt-get remove --purge hplip
- press enter and when required, type your password and press Enter again
 
Now download the latest HPLIP driver [from here]("http://hplipopensource.com/hplip-web/gethplip.html"). Make sure you download it in your /home/Download folder! Then open a terminal and then browse to the /Download folder:
> cd /Download
Now the .run file needs to be made executable, type this command: 
> [COLOR=black]sudo chmod +x {***}.run[/COLOR]
where {***} is the filename of the driver, you don't need to type the whole filename. If you type hp and then press the Tab key, you will see that the terminal fills in the whole filename for you. Press Enter and if required, type your password and press Enter again.
 
Now type the following command:
> ./{***}.run
This will execute the "installation wizard". At the beginning you be asked if the installation should be done automatically or custom. Choose custom here since we want to control the installation procedure. Also when you get questions about installing options like Jetdirect and Fax, answer all questions with Yes (**Y**). It will also ask you to remove older versions, answer with Yes, even if you removed older versions yourself manually. The best part of the installation procedure is that it checks and installs for missing dependencies. If you get the questions whether the installation procedure should install the missing packages four you, answer with Yes (this saves you a whole lot of time ;-) ). When the installation is finish you will be asked to reboot, plug-in the printer and 1 or 2 options more, always choose for reboot! After reboot, login to Ubuntu and when you're logged in, turn on your printer. If the installation went well, your printer should be recognized automatically.

---

