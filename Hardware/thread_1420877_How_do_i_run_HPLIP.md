---
title: "How do i run HPLIP"
date: 2010-03-03
forum: Hardware
---

### Post by jon-hhs on 2010-03-03
Hi I have a new printer that i want to add to my Jaunty machine, it is an HP Photosmart c4780, which i know is supposed to be fully suported by HP in Linux, I have been taken to the support page and downloaded the latest version of HPLIP, but this is just sitting on my desktop, as i don;t knwo how to make it run, please help

---

### Post by Jared Norris on 2010-03-03
To be honest the first thing I would do would be to try and install it from the drivers already included in Ubuntu. With Ubuntu most programs and drivers can be installed from within the operating system without having to go to third party websites to download drivers and updates.

To do this click on System > Administration > Printing to open the printing window.

Then click on the "New Printer" button and it will perform a search to try and locate your printer. It should come up with a list and you can select the one you want to install then press the "forward" button. This will then search for available drivers and give you any possible options. Select any options from the next screen (duplexer, etc) then hit the "forward" button again. It will ask you to specify a name for the printer and it's location then hit apply and tah dah you should be done.

If this doesn't work have a look at [http://ubuntuforums.org/showthread.php?t=1146161]("http://ubuntuforums.org/showthread.php?t=1146161") if you think you need the latest version (the one you downloaded off the website) and just change the file name in that post to the one you downloaded.

---

### Post by ajgreeny on 2010-03-03
Normally you don't actually "run hplip" in the way you seem to think, it just provides drivers for the printers.

What you can do, however, is make sure you really do have hplip installed from the repos, or the newest version (if it is needed for your printer model), direct from their website, and also install **hplip-gui** which gives you a HP toolbox, a terrific gui way of dealing with the maintenance and running of your printer/scanner.

---

### Post by syncmasterpt on 2010-03-03
You can run the HP toolbox...

In KDE -> alt-f2 and write hp-toolbox

---

### Post by blur xc on 2010-03-03
I installed hplip after downloading from the hp website and it is far superior to what is included by default in Ubuntu.  On my 9.04 I could not scan, nor fax, but after installing hplip every function of my printer works 100%.  In Karmic, I could not fax out of the box, but can after installing hplip.

I'd recommend it to anyone.  Plus, I now have my cool little hp applet in my top panel :D, and in the little printer dialog icon for my printer actually looks like my actual printer!  Whoo hoo!

So - the instructions to run it are right there on the hp website.  It's really not hard- but you have to run it from the terminal.  If it is on your dekstop, go to Applications -> Accessoris -> Terminal.  When that opens you will have to change your working directory to where the hplip.run file is located - "cd Desktop".  

From ther you can run it- I don't EXACTLY remember how to run it from memory, and it appears as though the hplip website is currently down for maintenance.  But it's something "bash ./hp*.run".  You can use bas auto-completion to fill in the super long file name, just type the first one or two characters and hit your Tab key and the rest will fill in.

Then follow the prompts on the screen.

BM

edit- also, if I recall right, you don't need to run it w/ sudo, but at some point during the install it will ask for your user password.  When you enter it, you will not see any output on the screen (as if it isn't working), but it is- just keep entering it and press enter when you are done.

---

### Post by jon-hhs on 2010-03-04
I have done what you say and it all runs through great until it trys to setup the printer, I select he wireless 802.11 option, connect the temporary USB it asks for and it detects the printer and tells me it is setup and that i can remove the usb, when i do so the installer goes on to the discover devices page and can't find the printer.  The only other thing i get is a window pops up from HPLIP saying system tray not detected on this system exiting, with only an ok box to click. Any ideas?

Update:

For some reason i had to go through the wireless/802.11 option and once it had set up the network connection, go back and select the other network option and tell the system the IP address that had been assigned, from there on, it worked fine. Thank you all for you help

---

