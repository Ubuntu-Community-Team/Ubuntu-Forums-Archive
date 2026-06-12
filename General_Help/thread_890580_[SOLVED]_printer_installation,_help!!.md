---
title: "[SOLVED] printer installation, help!!"
date: 2008-08-15
forum: General Help
---

### Post by Camilia on 2008-08-15
I put the cd from my printer, hp deskjet, into the tower and get a disk icon on the main page. I click and see a lot of folders. I am at loss as to what to do. In windows I just put my cd in the tower.

Tried to follow these instructions:
launch Synaptic, press System &#8594; Administration &#8594; Synaptic Package Manager. You need administrative access to use Synaptic; see Administrative Tasks for more details. Unlocked administrative task first.

What do I do? It is an hp deskjet 3930. Using ubuntu 8.4 Hardy heron

Perhaps it would be easier to reinstall windows and then convert everything?  That is basically how I have my internet connection.

---

### Post by coffeecat on 2008-08-15
With a HP Deskjet it's more than likely that the drivers are already present. Have you tried switching the printer on? If it's supported, it should be autodetected and a message balloon will pop up* telling you it's installed. Or, if this doesn't happen, switch the printer on and go to System > Administration > Printing and see if it's been detected there.

Post the model number of your deskjet and we can see if it's listed in [http://www.linuxfoundation.org/en/OpenPrinting](http://www.linuxfoundation.org/en/OpenPrinting) .

*** Edit**: at least, that's what happens in Hardy Heron 8.04. Which version of Ubuntu are you using?

---

### Post by Camilia on 2008-08-15
Oh!! It is very different from windows. I turned it on, clicked the brand, hp, and then in next screen click make default. Abra cadre it works!!

Thanks a bunch!!!

I tried to working it via the instructions at help.ubuntu.com but they didn't work. 

Now only have to figure out how to get adobe flashplayer 9 and my sound working. I got flashplayer 8 downloaded but doing the same isn't getting version 9 down.  Need it to hear news at comcast.net

---

### Post by coffeecat on 2008-08-15
> **Camilia said:**
> Oh!! It is very different from windows.

Oh yes. Much easier! :wink:

> **Camilia said:**
> Now only have to figure out how to get adobe flashplayer 9 and my sound working.

Go to System > Adminstration > Synaptic Package Manager and look for the package flashplugin-nonfree. Mark for installation and click on Apply. You should be good for Adobe flash player 9 with that. You will need to start a new thread for your sound problem.

---

### Post by Camilia on 2008-08-16
> **coffeecat said:**
> Oh yes. Much easier! :wink:



Go to System > Adminstration > Synaptic Package Manager and look for the package flashplugin-nonfree. Mark for installation and click on Apply. You should be good for Adobe flash player 9 with that. You will need to start a new thread for your sound problem.

Yeh, I have a tread for both problems. Just wanted to see if you new of anything, I could do. 

Tried the suggestion but still get the notice to download adobe flash player 9. Downloaded the tar.gz form and marked save with archives. Still no film.

---

### Post by Camilia on 2008-08-20
I thought the printer, hp deskjet 3930 was working but it is not. Not printer or icon showing.

Checked in the add programs and see items for printer installed. Did System > Administration > Printing and saw my printer listed. 

What else can I do?

---

### Post by coffeecat on 2008-08-20
> **Camilia said:**
> I thought the printer, hp deskjet 3930 was working but it is not. Not printer or icon showing.

Checked in the add programs and see items for printer installed. Did System > Administration > Printing and saw my printer listed. 

What else can I do?

I'm not quite sure what you mean. Have you ever managed to print out a page from it? If you have and it's listed in System > Administration > Printing it should work. Check all the usual things such as has the USB cable got loose, is the printer switched on (yes, I've done that! :oops: ) and so on. If you still can't get a page printed, open Firefox and type 'localhost:631' (no quotes) in the address bar. That's the CUPS (Common Unix Printing System) administration and setup utility. Click on the Printers tab and make sure your HP is set as the default. Then click on the 'Print Test Page' button to make sure it's working OK.

**Edit**: Another thought. Open the Synaptic package manager and make sure you have hplip installed. Mark the package hplip-gui for installation and install it. Now go to System > Preferences and select HPLIP Toolbox. It's indispensible if you have a HP printer. You can check other things in the toolbox such as ink levels and printer settings.

---

### Post by Camilia on 2008-08-20
I wasn't able to print a document 1st try. Tried again and clicked areas where print options came up and got it to print. Simply had to change pdf to printer. Embarrassed!! Was hoping no one noticed I had made it unresolved.

---

