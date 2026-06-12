---
title: "NVIDIA video driver won't allow mirrored displays with multiple monitors?"
date: 2010-11-02
forum: Hardware
---

### Post by JonnehD on 2010-11-02
Hello, everyone. 
I'm running a fresh install of Ubuntu 10.10 with the recommended proprietary NVIDIA driver installed.  
I'm using two monitors- one 37" Insignia TV, attached via DVI to VGA wire;  and a 17" acer monitor attached with a regular VGA cable. 

Before activating the NVIDIA driver, I was able to mirror the output to both of my displays, but the resolution wasn't large enough and I needed to activate the driver for gaming.  After activating, there doesn't appear to be any way to actually mirror the display in the NVIDIA x-server settings.  

Using the Separate x-screen and twin-view options aren't what I'm trying to do, I simply want to mirror the display with a resolution of 1360 x 768.

Is there any way to do this?  I'd rather not have to revert to windows as I just installed over it, but windows 7 did mirror the displays by default without any issues. :(

---

### Post by mutex023 on 2010-11-02
In the Nvidia settings tool, after selecting the second display (you might have to hit 'Detect Displays' first), select TwinView, then click on configure and select 'Clones', then hit apply. You can also change the resolution from 'Auto' to whatever you want.

---

### Post by JonnehD on 2010-11-03
Thanks for your reply.
I'm looking around the Nvidia settings and I can't find the 'clones' option.  I checked the "configure" button, but it still presents the same 3 options (disabled, twinview, separate x screen).


Edit: 
Nevermind!  I found it in the position settings!  

Thanks for your help! <3

---

### Post by mutex023 on 2010-11-03
> **JonnehD said:**
> 
Edit: 
Nevermind!  I found it in the position settings!  
<3

Yes, I forgot, its in the position option. My mistake.

---

### Post by jemssmith on 2010-11-03
First Check You have installed proper hardware driver for your Video Adapter. Then You can see your Device Manager and can check your Device Status whether it is properly working or not. It might be Your NVIDIA Video Card's physical problem. For further assistance you can contact NVIDIA's Support Team.

---

### Post by mutex023 on 2010-12-12
Usually I mirror my display to a sony lcd tv to watch movies. This meant that the cloned display on my laptop was not required. I searched around the net to find out how to enable only one display in cloned mode, but could not find any help. Turns out its very easy, using the same nvidia settings tool.

All you have to do is, after setting up the cloned output, select the laptop display, and click on configure, select Disabled, and hit Apply. Now the display is only on the TV and the laptop lcd screen is disabled.
Hope this helps others on the forum who are looking for a similiar setup.

---

