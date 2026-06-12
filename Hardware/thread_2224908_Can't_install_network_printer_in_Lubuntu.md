---
title: "Can't install network printer in Lubuntu"
date: 2014-05-18
forum: Hardware
---

### Post by prickett2 on 2014-05-18
I have a network printer hosted on Windows 7 that all my Windows machines can successfully print to.  I installed the unified Samsung drivers, then went to "Add Printer".  I successfully found the network printer.  Next, it chose "Set authentication details now" in the Authentication section and entered the Win 7 username and password.  "Verify..." confirmed all was well.  I clicked the "Forward" button and the waiting cursor appeared.  It just sits there with the waiting cursor spinning, but not seemingly doing anything else.

What is wrong?  How can I debug this?

---

### Post by pdc on 2014-05-18
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

have a read through this; 

see if it is helpful

---

### Post by prickett2 on 2014-05-19
That shows the steps I took to try to set up the printer.  My problem is when I click the "Forward" button and nothing further happens.  They don't mention that part in the document ;)

---

### Post by mastablasta on 2014-05-19
and the printer is not installed? how did you install the samsung drivers? did you install all components necessary for printing over the net? what model do you have?

---

### Post by pdc on 2014-05-19
when I go through the steps you did; to Add a printer; it halts on the forward key; because the details in the window are not complete;

You can see I have clicked on capt printer; and the device URI section is not completed; so it will not allow me to move forward;

A forum can be like a poker game; you have a series of cards we can't see; sometimes you have to disclose more; all said in a kindly way;

---

### Post by mastablasta on 2014-05-20
well in OP case they have to go to windows samba and then put the link inside where the printer is (hopefully it sees it). if it doens't see the printer then smbtree command should show it.

---

### Post by prickett2 on 2014-05-20
> **mastablasta said:**
> and the printer is not installed? how did you install the samsung drivers? did you install all components necessary for printing over the net? what model do you have?

The printer is not installed on the Linux box if that is what you are asking.  It is installed on the Win 7 box.  Installed the universal Samsung drivers from the package manager.  Not sure if installed all that is necessary - I don't know what all is necessary.  I was expecting the package manager would know that.  Am I wrong there?  I have the ML-2010.

---

### Post by prickett2 on 2014-05-20
> **pdc said:**
> when I go through the steps you did; to Add a printer; it halts on the forward key; because the details in the window are not complete;

You can see I have clicked on capt printer; and the device URI section is not completed; so it will not allow me to move forward;

A forum can be like a poker game; you have a series of cards we can't see; sometimes you have to disclose more; all said in a kindly way;

I get beyond the point you show in the screen shot.  It found my printer, it asked for my credentials (and then verified they were correct).  Only then did I hit the "waiting forever" forward button.  If the screen was not complete, I expect the waiting cursor wouldn't display.  It would be the arrow cursor.  So, to my _newbie _eyes, it appears its trying to do something.

---

### Post by prickett2 on 2014-05-25
I upgraded to the latest Lubuntu release and this time got an error message.  I solved the problem by installing Mint linux.

---

