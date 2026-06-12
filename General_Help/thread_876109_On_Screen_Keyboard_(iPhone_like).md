---
title: "On Screen Keyboard (iPhone like)"
date: 2008-07-31
forum: General Help
---

### Post by bl3nd3r on 2008-07-31
I am wondering if there are currently and onscreen keyboards that only become active when a text box is clicked. I have an application that requires input for 3 text boxes (first name, last name, and id number) and was hoping to find an onscreen keyboard that would appear when I click on one of the text boxes. 

I know that the iPhone has an onscreen keyboard that works like this, as well as another program I have used (Centrafuse). If anyone knows of a program that can do this I would love to know.

Thanks!

---

### Post by fadumpt on 2008-08-04
My friend has a Toshiba Portege M200 tablet running Ubuntu and one of the last bits of functionality he is looking for is this exact feature.  

To be able to tap a text box and have an input keyboard/handwriting recognition box pop up, or a button to that like on Tablet PC Windows.

I think he is trying to write something for Metacity or GTK to do this.

I'll keep the thread updated on progress, if any.
I have a Portege M200 coming in as well so this is an interesting topic.

---

### Post by bl3nd3r on 2008-08-04
> **fadumpt said:**
> My friend has a Toshiba Portege M200 tablet running Ubuntu and one of the last bits of functionality he is looking for is this exact feature.  

To be able to tap a text box and have an input keyboard/handwriting recognition box pop up, or a button to that like on Tablet PC Windows.

I think he is trying to write something for Metacity or GTK to do this.

I'll keep the thread updated on progress, if any.
I have a Portege M200 coming in as well so this is an interesting topic.

That sounds great! Yeah I would really love this feature but still haven't been able to find a suitable full screen keyboard application that this would work for.

Please keep me updated on any progress that your friend makes.

---

### Post by Robyr on 2008-08-05
For the record, I am Fadumpt's friend. Yes, I will be coding a workaround into CellWriter for this. On a related subject, I will also attempt to add as many tablet friendly changes as I can to the Launchpad for Ubuntu. Out of curiosity, what type of tablet do you have? If this is popular enough I'll focus more energy on it.

---

### Post by bl3nd3r on 2008-08-05
> **Robyr said:**
> For the record, I am Fadumpt's friend. Yes, I will be coding a workaround into CellWriter for this. On a related subject, I will also attempt to add as many tablet friendly changes as I can to the Launchpad for Ubuntu. Out of curiosity, what type of tablet do you have? If this is popular enough I'll focus more energy on it.

I am actually making my own tablet. Basically it will be a small, low powered computer (eBOX-2300SX) with a touchscreen as the interface. The reason I only need a low powered computer is that I will be using this for a single program that requires very little processing power.

Do you happen to have a time frame on when this should be ready?

---

### Post by Robyr on 2008-08-06
No idea. Basically, I want to patch Cellwriter to detect input events and raise from notification tray. If you would like to help, I will set up a small SVN branch we can work out of. It really shouldn't be that bad (aside from learning the bits of GTK I really ought to know), but I have a day job that is fairly demanding. Let me know if you have some ideas, and if you haven't tried Cellwriter, you really need to.

---

### Post by fadumpt on 2008-08-09
Welcome to the thread R0byr...get Something online so l can look into this as Well

---

### Post by bl3nd3r on 2008-08-27
> **Robyr said:**
> No idea. Basically, I want to patch Cellwriter to detect input events and raise from notification tray. If you would like to help, I will set up a small SVN branch we can work out of. It really shouldn't be that bad (aside from learning the bits of GTK I really ought to know), but I have a day job that is fairly demanding. Let me know if you have some ideas, and if you haven't tried Cellwriter, you really need to.

Sorry for the long absence. 

In terms of Cellwriter, it seems like a cool piece of software, however, I require more a keyboard then writing recognition as the user will be using their fingers, not a stylus. 

The main purpose for this idea has kind of gone away as I am short on money to get my tablet right now. I may continue with this in a few months, but please keep me updated on your progress.

---

### Post by fadumpt on 2008-08-27
Cellwriter has a Keyboard..press the keys button

---

