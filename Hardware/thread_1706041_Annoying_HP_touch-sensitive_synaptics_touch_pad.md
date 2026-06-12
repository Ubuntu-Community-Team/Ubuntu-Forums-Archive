---
title: "Annoying HP touch-sensitive synaptics touch pad"
date: 2011-03-13
forum: Hardware
---

### Post by ayqazi on 2011-03-13
Hi,

I got a new laptop - an HP Pavilion DV6 manufactured around the end of 2010 - and I have a major problem with the touchpad.

From what I've been able to tell, here is how it works:

There is only one button at the bottom base of the touch pad.  The Windoze drivers manage to make it work as 2 buttons, because button is actually touch-sensitive and part of the touch-pad itself.  So the windows drivers must, on detecting a click, use the position of the finger to decide whether or not it was a left or right button click.

As mentioned, the button is touch-sensitive, and part of the touch-pad.  Dragging my finger across it moves the cursor just as if I was dragging my finger across the main touch-pad.  The only thing indicating it is even there is a line painted horizontally across the top of it.  Unfortunately, in Ubuntu, holding down the button also counts as a cursor moving event, and then when I try to click and drag, the cursor jumps all over the place because of the multi-touch nature of the whole thing and the fact that I have two fingers on the touch-pad.  Also, clicking the button makes the pointer move all over the place while my finger clicks, because it is touch-sensitive and it picks up my finger movements across it as I press down.

It is multi-touch capable.  So the Windoze drivers obviously use this to allow a person to click and drag - one finger is on the 'mouse button' holding it down, and another finger drags across.  However as noted above, in Ubuntu, the cursor jumps all over the place because it tries to move the mouse according to the movements of both fingers that I use for clicking and dragging (yes, I have fat fingers and can't hold one of them perfectly still as I hold down the button).


Has anyone got this working like a normal touch-pad under Ubuntu?  Sorry if the above was confusing, but I don't quite know how to describe this all.

Thanks, regards,
    Asfand

---

### Post by DRohrbaugh on 2011-03-13
> **ayqazi said:**
> Hi,

I got a new laptop - an HP Pavilion DV6 manufactured around the end of 2010 - and I have a major problem with the touchpad.

From what I've been able to tell, here is how it works:

There is only one button at the bottom base of the touch pad.  The Windoze drivers manage to make it work as 2 buttons, because button is actually touch-sensitive and part of the touch-pad itself.  So the windows drivers must, on detecting a click, use the position of the finger to decide whether or not it was a left or right button click.

As mentioned, the button is touch-sensitive, and part of the touch-pad.  Dragging my finger across it moves the cursor just as if I was dragging my finger across the main touch-pad.  The only thing indicating it is even there is a line painted horizontally across the top of it.  Unfortunately, in Ubuntu, holding down the button also counts as a cursor moving event, and then when I try to click and drag, the cursor jumps all over the place because of the multi-touch nature of the whole thing and the fact that I have two fingers on the touch-pad.  Also, clicking the button makes the pointer move all over the place while my finger clicks, because it is touch-sensitive and it picks up my finger movements across it as I press down.

It is multi-touch capable.  So the Windoze drivers obviously use this to allow a person to click and drag - one finger is on the 'mouse button' holding it down, and another finger drags across.  However as noted above, in Ubuntu, the cursor jumps all over the place because it tries to move the mouse according to the movements of both fingers that I use for clicking and dragging (yes, I have fat fingers and can't hold one of them perfectly still as I hold down the button).


Has anyone got this working like a normal touch-pad under Ubuntu?  Sorry if the above was confusing, but I don't quite know how to describe this all.

Thanks, regards,
    Asfand

I am having a similar experience, i am using an HP 4510s, my cursor sometimes just takes flight, sometimes when trying to select, it moves upward when you remove your finger to press the bar to execute your selection. Just seams to be super sensitive in Ubuntu. I have 10.10.27.. I have went into the mouse menu and reset my sensitivity there, and it did seam to help somewaht, but it still has it's times.

---

### Post by Euboon2 on 2011-04-08
Similar problem for Debian Squeeze/Wheezy. I install kernel 2.6.38-2 and I can "right-click" by having one finger on the pad, while a second finger pressing down on the button. Effectively a right-click, but would be better if it can really do the usual right-click as in windoze. This series of Hp touchpad has been around for quite some time already, but apparently linux still does support it out of the box. Sigh...

My laptop is Hp-dv5t, bought last December.

---

### Post by Yellow Pasque on 2011-04-08
I hate my touchpad on my dv6-3210 (sensitive,jumpy). I can't remember if it worked better in Win7..

---

