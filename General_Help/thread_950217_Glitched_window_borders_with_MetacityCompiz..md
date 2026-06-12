---
title: "Glitched window borders with Metacity/Compiz."
date: 2008-10-16
forum: General Help
---

### Post by Ohht on 2008-10-16
So I finally decided to change my desktop a bit and use the New Wave theme that's included with Intrepid. Unfortunately a glitch causes my window borders to turn white and lose their buttons at random intervals (usually only for a few seconds at a time). I know this isn't an Intrepid issue as I had the same problems with around eighty-percent of the themes I tried (including the default Human theme) in Gutsy and Hardy as well when Compiz was active.

It happens often enough to be distracting, and while I've been able to temporarily fix the issue by disabling Compiz, I'm hoping there's some setting I can tweak somewhere to alleviate the problem as I'd like to be able to have my cake and eat it too, so to speak.

---

### Post by Ohht on 2008-10-26
Bump.

---

### Post by Jæd on 2008-10-26
I've got this as well. 

Steps to reproduce:

1) Set "Window Preferences" -> "Select windows when the mouse moves over them" to checked
2) Open three overlapping windows
3) Roll mouse across the three windows. After a few times at least one window title will glitch.

Interestingly, if make a theme with "Windows Border" as Crux, and Controls/Icons as "Human" with a default pointer I don't get this.

---

### Post by Ohht on 2008-10-26
Yeah I get it with Human/New Wave/Dark Room/Dust, but I don't get it with Clearlooks and a few others. It happens often enough that it's extremely distracting and takes away from the general good looks of the new themes.

---

### Post by Jæd on 2008-10-27
Appears to be a bug with a Nvidia driver. I have a MSI GeForce 7300GT 256MB, using the 177 driver. 
[https://bugs.launchpad.net/bugs/99508](https://bugs.launchpad.net/bugs/99508)

---

### Post by Yashiro on 2008-10-27
Try disabling mipmaps options in every plugin and in the general options of [COLOR="Green"]ccsm[/COLOR].

---

### Post by Jæd on 2008-10-29
> **Yashiro said:**
> Try disabling mipmaps options in every plugin and in the general options of [COLOR=Green]ccsm[/COLOR].

I don't have any options that are called mipmaps in Compiz Config Settings Manager... Or ist in something else...?

---

### Post by Yashiro on 2008-10-30
If non of your enabled modules within Compiz Config Settings Manager have a mipmap option then it's not related to that.

---

### Post by sceazy on 2008-12-23
I know this is an old post, so I dont know if someone else has found a solution to this, but I was suffering the same problems, and found this post, as well as what, so far, appears to be a kind of fix to it.  

I installed Ubuntu Tweak, and in the Desktop -> Windows section, you can set the transparency level of the metacity decorator, and I first tried setting the "Inactive window shade transparency level" to 1 (to make it so it doesn't change transparency when the window is inactive) but that just made it much worse.  So then I tried setting the inactive AND active window transparency level to have just a bit of transparency, (both values to something like 0.99) and no more glitching window borders!  Not sure why, but it seems to be working so far.  
So I'm posting this fix here cause this is the first post that popped up when I googled the problem... hopefully it'll help someone else too.

---

