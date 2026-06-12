---
title: "bluetooth mouse from Dell not working like it should"
date: 2008-05-21
forum: Hardware
---

### Post by karasuman on 2008-05-21
I'm still on hold with Dell, and I don't have very high hopes for their tech support being very helpful, anyway.  For one thing, the last person I talked to asked me what ubuntu was (thanks, guys, you installed it on my laptop!), and I keep wanting to ask them who told them to include "may I have your name" as part of their standard greeting.

But I digress.

Along with my Inspiron 1525 laptop (running Ubuntu 7.10), I also purchased a bluetooth keyboard/mouse set.  I figured I could use the keyboard with my PS3 (which I can; it works great) and the mouse with my laptop, and avoid the hassle of a USB mouse constantly having a receiver plugged in.

That's where I'm running into trouble.  I can get the mouse to work if I plug the receiver in as long as I do so after turning on my computer and hit the bluetooth buttons on both mouse and receiver over and over.  Once it's connected, as long as I don't shut down or unplug the receiver, I'm good.  But I spent extra money on this because I don't want to have to deal with the receiver--the extra money on the mouse itself and an extra $20 to have an internal bluetooth card.  I'd really like to get my laptop to detect the mouse without the receiver.

Now, I have to warn anyone trying to help me...  I'm an ubuntu baby.  This is my first experience with any Linux OS, and a lot of it mystifies me.  I might need some pretty step-by-step (ie, click here) instructions to get anything done.  (I've seen some instructions on doing various things by typing some sort of command line...  I don't even know how to access a command line prompt.  I have no idea how to find/edit any ini files.  I'm sorry.  I really am a baby.  But I'm trying!)

I appreciate any help that you guys can give.  Thanks for your patience.  :)

---

### Post by kjbuente on 2008-05-21
Are you 100% sure that the mouse and keyboard are bluetooth? I have to ask because I've bought bluetooth mice and keyboards from many differnt vendors and they only came with a reciver that is part of a combo deal. I've also never noticed them having a connect button, (I've seen buttons that say "pair" on the kb/mouse, but never on the reciver). After I get them to pair restarting bluetooth, or the computer it's always connected. (Onced it's paired, it's paired, It'll connect automactily after that. That's what makes bluetooth special).

Basicly I'm saying it's not bluetooth. It's just a regular RF wireless keyboard and mouse. You have a link to the web of the product? I might be wrong, but I HIGHLY dought it...

---

### Post by karasuman on 2008-05-21
Here's the order summary from Dell:

item no. 310-7990	Bluetooth Keyboard and Mouse Black,English,Dell OptiPlex Precision,Latitude, Customer Install

Here's the link to the product page: [http://accessories.us.dell.com/sna/products/I_O_Devices/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=310-7990]("http://accessories.us.dell.com/sna/products/I_O_Devices/productdetail.aspx?c=us&l=en&s=dhs&cs=19&sku=310-7990")

It says bluetooth all over it... on the keyboard, mouse, and receiver, and the icon next to the button is the little thing that looks like pointy glasses on their side (to me, anyway) that's also next to a little light on my laptop to show when it's working.

I just don't get why it won't work without the receiver.

In my laptop order summary, it includes the line:
430-2348	Dell Wirless 355 Bluetooth Mod

which, as far as I can tell, represents the bluetooth card I added to the purchase specifically so I wouldn't have to use the receiver.

Honestly, I'm completely stumped.

---

### Post by karasuman on 2008-05-21
Okay, I win.  

I still don't know what I'm doing at all, but typing this in the terminal worked:

sudo hidd -s
(press button on device)
(hit enter)
(win)

Now I don't need the adaptor connected to use my mouse!

---

### Post by kjbuente on 2008-05-21
I've edited my post because you posted before I was finished! Pleased to see that you got it working!

Perhaps instead of "Veni, Vidi, Dormivi" you should have "Veni, vidi, vici". Since you really have.

---

