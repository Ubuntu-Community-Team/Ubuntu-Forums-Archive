---
title: "there is no sound any more in my linux, I don't know how to fix it"
date: 2009-05-08
forum: Hardware
---

### Post by oren tal on 2009-05-08
I have update my linux to 9.04 before a few days, and since then (I am not sure if  immediately) I can not hear  sound in my linux.

When I boot to windows, I do hear sound, so I know it is not an hardware problem.
Also the linux before work with sound and I could listen to music and movie.

But now I can not and I can't get why.
:confused:

---

### Post by ahbart on 2009-05-08
Did you check all the volume levels and mute switches/checkboxes in gnome volume applet/manager?

---

### Post by b@sh_n3rd on 2009-05-08
Check if "User Priviledges" in "Users and Groups" have "Sound devices" enabled. What is your sound card? Sometimes, you may have to load your drivers...err..."soundcard drivers" that is..:D. After you make sure the above in "Users and Groups" are enabled, try "alsamixer" in a terminal...If it works without displaying an error message, sound oughta work...

---

### Post by oren tal on 2009-05-08
> **ahbart said:**
> Did you check all the volume levels and mute switches/checkboxes in gnome volume applet/manager?

yes, it is NOT on mute and the volume are set to the highest.

---

### Post by khelben1979 on 2009-05-08
Have you tried [AlsaMixer]("http://en.wikipedia.org/wiki/Alsamixer")?

---

### Post by oren tal on 2009-05-08
> **b@sh_n3rd said:**
> Check if "User Priviledges" in "Users and Groups" have "Sound devices" enabled. What is your sound card? Sometimes, you may have to load your drivers...err..."soundcard drivers" that is..:D. After you make sure the above in "Users and Groups" are enabled, try "alsamixer" in a terminal...If it works without displaying an error message, sound oughta work...
Thanks.
who can I do this check?

As for my sound card, I think it is on board, I check the list of my computer item and I don;t find there sound card so I think it is on-board sound card.
The computer is ASUS.

---

### Post by oren tal on 2009-05-08
> **khelben1979 said:**
> Have you tried [AlsaMixer]("http://en.wikipedia.org/wiki/Alsamixer")?

no, but I don't see how can it help me.
There is no sound at all.
Even if I go to you-tube to watch movie then still I don't hear anything.

anyway thanks.

---

### Post by oren tal on 2009-05-08
> **khelben1979 said:**
> Have you tried [AlsaMixer]("http://en.wikipedia.org/wiki/Alsamixer")?

I have installed it right now.

I will restart and see if it can work out.

---

### Post by oren tal on 2009-05-08
> **oren tal said:**
> I have installed it right now.

I will restart and see if it can work out.

I have restarted my computer and the device driver is AlsaMixer.
I go to youtube and I still hear nothing.

maybe it is about User Priviledges setting.
However I believe it is already enable.

How can I check it.

---

### Post by oren tal on 2009-05-08
I wrote alsamixer in the terminal and this is what I got.
[IMG]http://farm4.static.flickr.com/3392/3511977785_aca08e5494.jpg?v=0[/IMG]

Maybe it can help you.

Thanks.

---

### Post by Goddard on 2009-06-04
That did it!!! FOR ME YES!!

---

### Post by khelben1979 on 2009-06-05
If your sound still isn't working, this can mean that your new Linux kernel has no support for your soundcard/soundchip. In this case you can always download the alsa source code, unpack, configure and install it.

[ALSA SoundCard Matrix]("http://www.alsa-project.org/main/index.php/Matrix:Main") displays supported soundcards/chips.

[How to install ALSA from source]("http://www.alsa-project.org/main/index.php/Download")

---

### Post by ahbart on 2009-06-05
> **oren tal said:**
> I have update my linux to 9.04 before a few days, and since then (I am not sure if  immediately) I can not hear  sound in my linux.
I doubt it is a problem of the kernel not supporting this soundchip, because it worked before on a previous install. It is very unlikely that a sound chip is no longer supported. 

You might want to google on your sound chip. 
lspci in a terminal can give you more information.

---

### Post by khelben1979 on 2009-06-05
> **ahbart said:**
> I doubt it is a problem of the kernel not supporting this soundchip, because it worked before on a previous install. It is very unlikely that a sound chip is no longer supported. 

You might want to google on your sound chip. 
lspci in a terminal can give you more information.

Very unlikely yes, but it is possible to create a Linux kernel where you choose to scale it down, remove unwanted drivers etc etc.. and I don't know what's included in an Ubuntu Linux kernel.

---

