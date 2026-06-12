---
title: "Dual Monitor Issues in Ubuntu 12.04"
date: 2012-06-29
forum: Hardware
---

### Post by Jnk1296 on 2012-06-29
So I recently decided to dual boot my Windows PC with Ubuntu using the WUBI installer, and it worked perfectly. My wireless hardware worked instantly, and everything was flawless. But for some reason I can't seem to get Ubuntu to work with my two 'monitors' (i put the word monitors in quotes because one monitor is actually my Sony Bravia.)

I've seen this problem described on many different thread. My main monitor works perfectly, white my TV gets only a white screen with an 'X' cursor. The right click menu works on it, and that's it. And this was only achieved after enabling it through Nvidia's control panel.

My graphics card is an EVGA GT430. And I'd love to get these monitors working, as they worked flawlessly in Windows 7.

---

### Post by Jnk1296 on 2012-06-29
Okay, so I enabled Xinerama and managed to get rid of the white screen and get both monitors working, but now there's a new problem. Unity doesn't load anymore. I have no way to access Terminal, any of my programs, and anything. I had to do a trick I learned in WIndows to get my browser opened, and so now I'm stuck. Help please? xD

---

### Post by Jnk1296 on 2012-06-29
Okay, so I managed to uninstall the nvidia driver, and that not only got the Unity problem fixed, but now I have both monitors working? Except now my cursor movement is a bit stuttered and laggy, and there appears to be a wall between the two displays. I can move windows from the second monitor the the primary one, but i can't move windows from the primary to the secondary. And what happens if I reinstall nvidia?

---

### Post by arjenzwerver on 2012-06-29
Did you use Twinview or a seperate X-screen when enabling both monitors through the nvidia control panel?

---

### Post by Jnk1296 on 2012-06-29
I used x-screen. I will say, though, I reinstalled the nvidia driver, and now I'm back where I started. With one working monitor and another with no output.

---

### Post by arjenzwerver on 2012-06-30
You should use the NVIDIA X Server Settings and then enable the second display in 'X Server Display Configuration' using TwinView as Configuration.

---

### Post by Jnk1296 on 2012-07-02
Wow. Thank you. It really was that simple. I'd just assumed that, given the name, it would just duplicate my desktop onto the second monitor. xD Guess I should have checked it out better.

Thanks again.

---

