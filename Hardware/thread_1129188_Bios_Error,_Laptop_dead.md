---
title: "Bios Error, Laptop dead ??"
date: 2009-04-18
forum: Hardware
---

### Post by ronaldo07 on 2009-04-18
Hi guys,

I am new to Ubuntu. First I installed it on my main PC.
But I can not make it work completely so I went back to XP.

Now I am installing it on my 6 yrs old laptop. Something went wrong during it.

Installation went wrong because laptop shot off after sometime.
Now I am having weird problem.

Now when I start my PC it boot and stuck at black screen.
Only one line written on screen.

U1 BIOS.


Thats it, nothing happens. Pressing any key not doing anything.

Now I can not even go back to XP installation and not even ubuntu.

Is my Laptop dead??

---

### Post by coffeecat on 2009-04-18
This sounds like a problem with your BIOS. If you google "U1 BIOS" you'll find a few threads on other forums from people with the same problem. On one I found this:

> U1 Bios is your bios maker.  Universal Scientific Industrial (USI).... which doesn't help much.

Try googling "U1 BIOS" together with the make and model number of your laptop. You might be lucky and find a fix. What is the make and model?

Can you get into the BIOS at the POST screen to reset it? Another suggestion I found is to remove the CMOS battery and replace it. But not an easy job in a laptop, I fear.

---

### Post by ronaldo07 on 2009-04-19
Thanks for reply.

Unfortunately I did google before posting here.
And no one has any solution for it any where.

I found few posts similar to my problem but never got any final solution.

I was hoping someone here can help.
I will folllow your suggestions, I might just open my laptop.

Because its dead anyway :(

---

### Post by ddrichardson on 2009-04-19
CMOS battery shouldn't stop it posting. If the CMOS battery was failing you would have noticed the laptop needing its time and date re-entered on boot.

---

### Post by ddrichardson on 2009-04-19
What's the make and model?

---

### Post by ronaldo07 on 2009-04-19
it is HP ZE4125

I am about to open my laptop. Will update soon.

Thanks

---

### Post by ddrichardson on 2009-04-19
I'd be inclined to swap out the memory first off.

---

### Post by coffeecat on 2009-04-19
Yes, don't open the laptop just yet. I was wrong to suggest changing the CMOS battery.

You haven't yet said if you can get into the BIOS setup or not. You usually press del or F2 or one of a number of keys at the POST screen, but I'm not sure whether you are getting the POST screen (or a HP splash screen). Do you only get 'U1 BIOS' on a black screen, or do you see anything before that?

---

### Post by ronaldo07 on 2009-04-19
Thank god I did not open it yet :)

Ok so here it is.

As soon as I start my laptop, it goes to blank screen with 

U1 BIOS

Nothing else. No HP logo, No BIOS nothing.

I swapped memory. Nothing.
I removed HDD. tried to boot from CD. nothing

---

### Post by Sylslay on 2009-04-19
Can You load Bios GUI/
1/ Try load deflaut factory settings,
2/ Switch off unnessery IRQ requst for unused device like unuset parell port for printers, usb
3/ change list for defload booting,insteed from hddd, start 1st boot from CD
3/ Switch off QUICK BOOT, if any 
3/ Save and reboot

---

### Post by Sylslay on 2009-04-19
Sorry, read again, no bios GUI,,,
best option in this moment, is borrow from sombody RAM memory, and check if it will work instead Yours memory,,
often got balck screen whan memory is foulty, but usually it says abput it

---

### Post by sarang on 2009-04-19
Software installation (other than BIOS and microcode updates) should not ruin your BIOS. However, that seems to have been the case. I doubt it is your RAM / HDD. If the BIOS is fine but RAM is bad, most BIOSes will give out some error / beeps / etc. to tell you what's wrong. As this is not happening, I would say definitely the BIOS. Search for the BIOS recovery disk on your laptop manufacturer's site. There is often a link to it from BIOS update pages. Use that to re-burn your BIOS.

---

### Post by ddrichardson on 2009-04-19
If the RAM is not registered, as with CPU then you won't get a POST beep on most machines - it wont even start BIT, the power on self test needs to fetch/execute like any program.

You can try getting a BIOS flash disk but it depends on the hardware manufacturer and how they flash the BIOS, on an Aspire One for example you can do it by holding down Fn+Esc with a USB stick in and a specific file name.

If you can't boot at all then you can't do the generic HP boot disk/flash BIOS thing anyway.

---

### Post by sideaway on 2009-04-19
I'm pretty sure HP do a software flash like Asus do. As in, you need an OS... Or at least a live CD. Your best bet is to either send it back (if it's under warranty) or open it up and remove the (CMOS) battery for ten minutes.

Laptops aren't hard to dismantle, each laptop has a certain way to do it. There should be a guide for your particular model on the internet somewheree. Be careful not to snap any plastic. Give your heat sink a blast of air to clean it out too :) I even replaced the thermal paste on my video card and CPU when I last took mine apart. Oh and keep track of your screws, when I firts took mine apart I had three different looking screws left over... Had to take it apart again. Not fun :)

I found out I had a dead motherboard... Not that that's relavent, it just sucked :(

Have fun, hope you can fix your problem.

---

### Post by ddrichardson on 2009-04-19
Keep track of your screws by using a sheet of cardboard and pressing each screw into the cardboard in the same place as on the laptop. It sounds excessive but we do it on aircraft all the time - if a screw is put in slightly off then it will only want to go back in that hole.

---

### Post by ronaldo07 on 2009-04-19
Its a 6 yrs old laptop.
so no question about sending it HP and I am not gonna take it to any repair shop either.

I am going to open it. I think I will have fun with it.

I found BIOS but I don't know how to flash it.
I do NOT have floppy drive, I put downloaded file in USB but its not doing any thing.


I am going to borrow RAMs too to check if my RAM is bad.

---

### Post by ddrichardson on 2009-04-19
USB sticks need to be formatted as FAT16 if the BIOS accepts flashing from them.

---

### Post by ronaldo07 on 2009-04-19
Few updates

I opened my laptop :)
it was fun.

Resetted cmos but still same thing.
Made bootable USB but still nothing.

Next I am going to but new cmos as it is very cheap, nothing wrong in trying :)

Any other suggestions ?

---

### Post by ddrichardson on 2009-04-19
New CMOS is cheap because its only volatile memory. No point replacing it. Replacing BIOS might work though, just use a decent heatsink on the chip when you're de/soldering.

---

### Post by ronaldo07 on 2009-04-19
I looked into internet "how to replace BIOS chip"
not as easy as changing cmos battery :D
But I think I will go for it.

I don't see how can I make it worse. it not running anyway

---

### Post by ddrichardson on 2009-04-19
It depends on the type of flash RAM they used - it doesn't have a little opaque window on top of the BIOS chip does it?

---

### Post by ronaldo07 on 2009-04-19
No, no such window.

I found someone on ebay selling new BIOS chip for $12.
it will be programmed for my laptop model.

It should work. I have sent email, waiting for reply.
I will update soon

---

### Post by ronaldo07 on 2009-04-27
I have update, I got BIOS chip.
And bingo!!!!

That was the problem, somehow I damaged my older BIOS chip.
I am going to try to install Ubuntu, I hope this time it goes smoothly.

---

### Post by ddrichardson on 2009-04-27
I doubt you damaged it, some IC damage especially static damage can take years to manifest. Well done getting it swapped, let us know how you get on.

---

