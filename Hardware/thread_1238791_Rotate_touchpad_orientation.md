---
title: "Rotate touchpad orientation"
date: 2009-08-12
forum: Hardware
---

### Post by drewsus on 2009-08-12
Hello all!
So, I hope this is the best section to post this. 
I like to use my Acer Aspire One to read e-books and comics. And, as you might guess, I like to rotate my laptop (netbook) 90 degrees to better emulate the experience. Furthermore, I made a book stand of sorts to hold my laptop in that position on my desk.
I am using Ubuntu 9.04. 
I use the command "xrandr -o right" to rotate 90 degrees counterclockwise. I realize I can just rotate the view within a program like comix or document reader, etc, but that is not what I am trying to achieve. I want kmess, firefox, etc to be rotate as well and that is what I have achieved. 
However, the touchpad orientation stays the same and that means I need to move my finger up to make it go right, right to go down, etc. Thats hard on the brain!
SO, I need help with rotating my touchpad orientation as well as my screens orientation! How can this be achieved in Ubuntu 9.04?!

Thanks very much in advance!
dRewsus

---

### Post by drewsus on 2009-08-26
bump!
please, someone has to know. I can't be the only one interested in this and I cant imagine this is crazy hard

---

### Post by Kenai on 2010-02-02
I have the same question, so... threadbump.

Seriously, how would one go about this?

I have 9.10 netbook remix on an eee pc 900

---

### Post by NickJones on 2010-02-02
I've looked into doing this, and couldn't find any way to do it, short of re-writing drivers and I'm not smart enough to do that, so here are 2 options for you:

[LIST]
[*]Get a USB Touchpad and tape it sideways.
[*]Get a USB Mouse
[/LIST]
That's it.
Nick

---

### Post by Enalia on 2010-02-10
>     * Get a USB Touchpad and tape it sideways.
    * Get a USB Mouse

I have to be honest, such a response is not helpful.

I have the same question, and I've noticed there was a suggestion here:

[http://brainstorm.ubuntu.com/idea/20789/](http://brainstorm.ubuntu.com/idea/20789/)

Wondering if anyone knows any info about the progress of this?

---

### Post by pinkunicorn on 2010-03-31
I'm very interested in solving this as well.

---

### Post by IcarusR on 2010-04-01
This is what you are all looking for I believe...

[http://cc.oulu.fi/~rantalai/synaptics/]("http://cc.oulu.fi/~rantalai/synaptics/")

---

### Post by drewsus on 2010-04-01
I found that a few days ago,  and it is what we are looking for except.. for me anyway, I lost the ability to scroll on the touchpad. Redefining the touchpad boundaries did not work (or if so, for just a couple seconds). I had to reinstall the  original synaptic touchpad package from synaptic package manager to get scrolling working again.
Also, Im not sure if its related, but I also seem to have lost the ability to suspend/hibernate after doing this patch... (and still after reinstalling the originals)
Drew

---

### Post by IcarusR on 2010-04-01
> lost the ability to scroll 
Strange, others have had success with this. 
Did you check the synaptics settings to check that scroll had not been disabled ??

Just checked on the site I linked & found this near the bottom...

> Scrolling
Scrolling with swapped axis do not work correct. Somebody pointed me that we should not use hw->x = -ev.value; but hw->x = MAX_VALUE-ev.value;
But I do not know what is that MAX_VALUE. So if you figure it out, let me know it.

Instead you can tweak scrolling with some variables.

synclient LeftEdge = 1872
synclient RightEdge = 5072
synclient TopEdge = 1712
synclient BottomEdge = 4144


---

### Post by drewsus on 2010-04-05
Hmm, I'll have to look into this next week after finals! 
Only difference I see is that I didn't just lose the scrolling after performing a rotation. I had no scrolling upon normal orientation even after a fresh boot. Or, I should say, I could scroll for about 5 seconds then it was lost. 
But, like I said, I will try some things around the 14th!

---

