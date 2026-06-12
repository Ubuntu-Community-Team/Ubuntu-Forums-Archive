---
title: "Gutsy not working on new Sony Vaio"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by daz4126 on 2007-10-24
I've just bought a new Sony Vaio CR22G/W and tried to put in the Gutsy disc - it won't even boot into the live mode! I get the menu at the beginning and choose to run from the live disc. I then get the Ubuntu logo with the progress bar, but then I get just a coloured mess on screen. Wierd thing is that when I press the power off button, it produced the Ubuntu shutdown screen saying 'remove disc then press enter'. This indicates that Ubuntu was actually on, but with possibly with no graphics support???

Anybody got any experience of this sort of thing or ideas of what to do?

The laptop is a new model, so maybe some of the hardware is not supported - how long is it usually before it is supported?

thanks,

DAZ

---

### Post by Depressed Man on 2007-10-24
What graphics card is it? And what company (Nvidia, Intel, ATI?). You may need to install it with the alternate installer then enable the restricted drivers after.

---

### Post by daz4126 on 2007-10-24
Thanks for the reply. The graphics card is 'Mobile Intel Graphics Media Accelerator X3100'

How do I do the alternative install?

---

### Post by Depressed Man on 2007-10-24
You need to download the alternate ISO from Ubuntu. 

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Check the checkbox saying you want the alternate cd (text installer).

---

### Post by daz4126 on 2007-10-26
Thanks for that advice depressed man. I can't get access to a download at the moment, but will have a go at this later in the week. Will the text installer let me boot into the live CD or will I have to install it?

---

### Post by daz4126 on 2007-10-26
Has anybody had any experience with the intel graphics chips?

---

### Post by lenticular on 2007-10-26
I had the same problem with my Vaio TZ130.  I got around it this way:

1) boot from gutsy cd
2) Chose option 6 (or maybe it is F6)
3)  You will see the command line for the installation
4) Delete the last bit at the end about "quitet" and splash

You should get a text install that, all the same, boots you into Live CD.

Good luck.
-John

---

### Post by daz4126 on 2007-10-26
John - that is brilliant! I have finally managed to get Ubuntu on my vaio!!!

How did you find this out and why does it work??

I cheekily tried to used the visual effects, but it will only let me have the basic option. I guess that means that I have to install some graphics drivers. Does anybody know how to install the intel chip drivers?

Next job is to create a partition and try to do a full install.....

I realise that this is a new computer so will have problems like this. Has anybody had any past experience and found that they are sorted out in later versions of Ubuntu?

Thanks again John!

---

### Post by Depressed Man on 2007-10-27
You should see some notificaiton about restricted drivers. Or go to system > administration > restricted drivers.

Then install the intel ones (it'll probably be the only thing listed there). Your Intel chip is supported. It's just, need the drivers I think.

---

### Post by daz4126 on 2007-10-28
Okay ... now for my next problem!

The wifi is not recognised, so no internet at the moment. It is using this:

 	Integrated Wireless LAN IEEE 802.11b/g

Has anybody had any luck with getting this or any other vaio wifi to work? I could use a wired connection if anything needs downloading, but this wouldn't be a long-term solution.

DAZ

---

### Post by ArchiMark on 2007-10-28
> **lenticular said:**
> I had the same problem with my Vaio TZ130.  I got around it this way:

1) boot from gutsy cd
2) Chose option 6 (or maybe it is F6)
3)  You will see the command line for the installation
4) Delete the last bit at the end about "quitet" and splash

You should get a text install that, all the same, boots you into Live CD.

Good luck.
-John

This advice sort of worked for me too, John on my Vaio TZ150N.....

However, when Xubuntu booted up to desktop, the desktop took up only about 1/4 of the total display area and was located in the upper left of the display.

Any suggestions to get it to fill out the entire display?

Thanks,

Mark

---

### Post by lenticular on 2007-10-28
I wish that I could take credit for this, but I found it on another thread.  Of course, I've lost that thread so I can't even give credit to the person that helped me out!  It sure is nice to have work, though.

-John

---

### Post by daz4126 on 2007-10-28
> **Depressed Man said:**
> You should see some notificaiton about restricted drivers. Or go to system > administration > restricted drivers.

Then install the intel ones (it'll probably be the only thing listed there). Your Intel chip is supported. It's just, need the drivers I think.

I tried this and there were no references to intel graphics drivers, just one other thing that was already ticked. Do I have to do something else to install these drivers - add them in synaptic or something??

---

### Post by srirammurali on 2007-10-28
hmm. that sounds strange, i have been running gutsy without any issues so far on my vaio touch wood..

---

