---
title: "Brother MFC-495CW Wireless Printer"
date: 2010-02-13
forum: Hardware
---

### Post by Wolf197 on 2010-02-13
I currently own a Brother MFC-495CW Wireless Printer and it seems that the drivers aren't supported with Ubuntu. Am I correct in assuming this is true, or am I just not looking hard enough? I found a website hosted by the Brother company that lets you download drivers for their hardware. I downloaded the drivers (which come in both .rpm and .deb formats) and installed them successfully, but unfortunately when I find the printer, and it tells me to select the brand name and correct model. MFC-495CW does not appear on the list. I tried installing the drivers in both .deb and .rpm and still no success. I want to be able to install this as a wireless printer to avoid having extra cables in my house. Any suggestions?

---

### Post by lparsons21 on 2010-02-13
I have the 490CW and it works fine wirelessly.

Did you download and install both the CUPS and LPR drivers?  That's what I did for the 490.

---

### Post by Wolf197 on 2010-02-16
yes i did

---

### Post by brydonhunter on 2010-02-16
Works perfectly in 9.10 with printing, faxing and scanning all wireless. Also have it working perfectly with 9.04

Did you download the drivers from the Brother site? Follow the instructions exactly. Do you have error messages? Can you ping the printer, is IP setup correctly?

Let us know.

Scott

---

### Post by Wolf197 on 2010-02-18
everything seems to be set up correctly. the printer appears in my printing manager, but I can't connect to it. It's connected on the printer itself to my wireless, and my wireless on my laptop is working correctly. How do I connect the printer to the computer?

---

### Post by sgosnell on 2010-02-19
Try adding a new printer.  System/Administration/Printing, click on the New... button, and tell it to find a network printer.  It should find the printer and offer to install the driver.  I've never had that fail with a Brother.

---

### Post by Wolf197 on 2010-02-19
I actually did that several different times. It finds the printer. but apparently MFC-495CW drivers aren't supported. It brings up the list of printers and when I search through it, there isn't one for mine. I've also downloaded and installed the cupswrapper and lps drivers and they don't seem to have any effect.

---

### Post by Flendon on 2010-02-26
I just bought this same printer. I got it working with the directions on the brother page. You have to make sure to follow every step in order or it won't work. And if you get any errors about folders not being created, then create them with mkdir and rerun the last step.

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/index.html)

---

### Post by HookedOnFishing on 2010-03-10
Did you ever get it to work? I too have just came to the same stopping point you have. Followed all steps up to using USB cable to connect and test. Instructions appear to indicate you can test wireless without doing usb first. I cannot find my driver in the list in Cups. It does detect its name through Cups fine. Somebody help me. This printer is also a shared printer on a Windows 7 network. Is this going to be a problem? Please help me too.

---

### Post by HookedOnFishing on 2010-03-11
I finally got mine to work tonight. Dont know what I did but followed the instructions again and it worked. Everythng is working. I sent a pic of penguins from a network drive on my wife's XP laptop just for fun. It worked! I love Ubuntu! You  saved my old laptop!

---

### Post by duble08 on 2010-03-20
i just bought the same all-in-one printer/scanner/fax, and i'm running ubuntu 9.10 - i was looking for a compatible device for ubuntu when i bought it, and everything works beautifully!! i'm glad brother supports linux for their hardware! Just follow the directions on their web site and download their drivers for their printer, and for the scanner (i used the DEB packages), and everything works as it's supposed to!  I have it connected to my wireless network, and no USB connection was ever required to configure everything!  awesome stuff!

---

### Post by Wolf197 on 2010-04-09
I haven't been able to get it work. I go to the Brother website and seem to get lost in redirectories. Could someone please post the steps needed to install the drivers for the MFC 495CW printer here? It would be greatly appreciated.

---

### Post by dpj on 2010-04-09
You can access CUPS via your webbrowser by typing [http://localhost:631](http://localhost:631) into the url bar.

From there you can add the printer under "Adding Printers and Classes"

Hopefully the printer will be found automatically and you can proceed along to add the driver, which seems to be where you're having problems.

At some point it will give you a list of printers/drivers to choose from. Below that is a place where you can supply your own ppd. Click on that. The Brother driver should be found at:

/usr/share/cups/model/

It'll probably be called 'brmfc495cw.ppd'

If it's not there then I would think that the installation of the cupswrapper driver package hasn't gone correctly. Note that you first have to create the directory 'model' in /usr/share/cups/ before proceeding with the installation of the cupswrapper driver.

---

### Post by wojox on 2010-04-09
> **Wolf197 said:**
> I haven't been able to get it work. I go to the Brother website and seem to get lost in redirectories. Could someone please post the steps needed to install the drivers for the MFC 495CW printer here? It would be greatly appreciated.

[Go here]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#MFC-495CW") and download the LPR Driver and cupswrapper driver in deb format.

Download both of those to your /home directory. Don't open with gdebi.

Now open your terminal and proceed with the following:

```
sudo mkdir /var/spool/lpd
```

```
sudo dpkg -i --force-all mfc495cwlpr
``` <tab> # the tab button should finish the line.

```
sudo mkdir /usr/share/cups/model
```

```
sudo dpkg -i --force-all mfc495cwcupswrapper
``` <tab>

You should see something along the lines of
Unpacking
Setting up
* Restarting Common Unix Printing System: cupsd [ OK ]

---

### Post by tora201 on 2010-04-10
Did anybody try this bronter with Vuescan? Could you get it going??
It works fine with Xsane, but not recognized at all with Vuescan....
I am sure Vuescan needs to have a script to get it going, but I am not sure. Been searcing all day and failed to come up with a clear answer.

Cheers.

---

### Post by GrumpyOldGoat on 2010-04-15
I have crawled through the Brother website trying to figure out which files I needed, which ones I didn't need and searching through massive lists of printers that "do need this file, but do not use if your printer isn't listed, go to next step."

I worked my way through the 
"Required steps before installing anything".

Same stuff, use this step IF your printer is listed, if not go elsewhere....

I tried the steps list in a post above, only to discover that 'those steps' are good only if you do not have a 64 bit machine.

I have an AMD 64 Phenom Quad Core Processor.

While it would be nice to have the time to sit down and read the entire manual for Ubuntu, right now I just don't have that luxury.

I was using windows vista home premium 64 bit....

It has been exceptionally buggy since day one, various 'net framework' updates failed to install, and about a week ago it stopped responding to either my keyboard or mouse.

Now I'm forced into learning a system RIGHT NOW!
 While ms 'tech support' sends me one email daily asking if i tried booting into safe mode and did my keyboard work there?  If not, did the mouse?  If not did you boot from the original install disk?  Did you unplug all your USB accessories and try it?  etc.....

So, any help I can get that will put me in an operable condition will be GREATLY APPRECIATED.

Thanks,
Drew

---

### Post by sgosnell on 2010-04-15
It shouldn't matter if your system is 32-bit or 64-bit, the steps are the same.  All you should have to do is install the printer driver and the scanner driver.  The driver will be different, but everything else should be the same.  Download the appropriate drivers as Ubuntu .deb files, install with gdebi, and print/scan.

---

### Post by kai_kan on 2010-05-09
Any luck?

Still fighting this battle myself, getting my MFC-495CW to talk with 10.04 64-bit on my new machine. Have tried the recommendations here (and elsewhere on the net) to no avail.

Had no trouble with my old 32-bit machine... suspect the trouble is indeed in that. The drivers claim to be specifically for 32 bit.

Anyone get this working?

---

### Post by somanyquestionstoask on 2010-07-20
Mine is a duhhh problem...to receive a fax which button do i press...setup is all done etc....someone sent me or tried to send me a fax...phone rings...fax is ready...i hit start...guess wrong button cuz i dont see a thing lol...nowhere does it say how to actually receive a fax...what to press...do i actually answer the phone or does that cut off the fax..yes im duhhh me ..please help

---

### Post by sgosnell on 2010-07-20
The fax setup is on the printer.  You need to go into the menus on the printer and set up the fax as necessary.  Reading the manual that came with the printer might help.

---

