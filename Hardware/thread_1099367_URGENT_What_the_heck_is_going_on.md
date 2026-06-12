---
title: "URGENT What the heck is going on?"
date: 2009-03-18
forum: Hardware
---

### Post by TheSlav on 2009-03-18
Everytime I install my ati video card through hardware w/e. i restart my computer and it says "out of range" Current frequency being 5 digits over the required or something or other. How can i just install my video card and be able to boot without this. 


Also, when i restart repairing xserver (watever that does) my video card goes back to deactivated.

Please help guys and gals. this is making me want to go back to xp.

---

### Post by markbuntu on 2009-03-18
What card do you have?

---

### Post by thumper13 on 2009-03-18
> **TheSlav said:**
> Everytime I install my ati video card through hardware w/e. i restart my computer and it says "out of range" Current frequency being 5 digits over the required or something or other. How can i just install my video card and be able to boot without this. 


Also, when i restart repairing xserver (watever that does) my video card goes back to deactivated.

Please help guys and gals. this is making me want to go back to xp.

Sir, let me first start by saying your post doesn't have much information in it. Ati drivers are a hassle with ubuntu (I used to have the x200 in my computer, I upgraded to a nvidia card because of this.. Don't get me wrong, ATI is great in linux for everyday, but since I'm a gamer, the nvidia helped) "Out of range" was an error I was getting, however it wasn't ubuntu telling me this, it was my monitor rather, the Refresh rate was too high. The reason your video card goes back to "deactivated" (or the open source driver) is because reparing xserver makes it go back to the last working setup.

My advice is to activate the proprietary driver, then when you restart, click "options" on the login screen and pick "Fail-safe session". It is similar to booting the computer in safe mode on xp (to my knowledge anyways.) Then you will be able to change the refresh rate on your video card, etc. After your settings are correct, restart the computer and boot it normally, it should work. My x200 would do a similar thing, because the proprietary driver didn't like my display. These steps fixed my issue.

For the record, my pc was using an ATI x200m 512 mb with an AG Neovo f-417 display.

As far as going back to windows goes, perhaps another tidbit of advice may be to try dual-booting your computer with linux and windows for a while, to get the hang of linux. There are a plethora of guides available on the subject, and that way you'll never be boned without a computer if linux is acting strangely.

--T

---

### Post by TheSlav on 2009-03-20
> **thumper13 said:**
> Sir, let me first start by saying your post doesn't have much information in it. Ati drivers are a hassle with ubuntu (I used to have the x200 in my computer, I upgraded to a nvidia card because of this.. Don't get me wrong, ATI is great in linux for everyday, but since I'm a gamer, the nvidia helped) "Out of range" was an error I was getting, however it wasn't ubuntu telling me this, it was my monitor rather, the Refresh rate was too high. The reason your video card goes back to "deactivated" (or the open source driver) is because reparing xserver makes it go back to the last working setup.

My advice is to activate the proprietary driver, then when you restart, click "options" on the login screen and pick "Fail-safe session". It is similar to booting the computer in safe mode on xp (to my knowledge anyways.) Then you will be able to change the refresh rate on your video card, etc. After your settings are correct, restart the computer and boot it normally, it should work. My x200 would do a similar thing, because the proprietary driver didn't like my display. These steps fixed my issue.

For the record, my pc was using an ATI x200m 512 mb with an AG Neovo f-417 display.

As far as going back to windows goes, perhaps another tidbit of advice may be to try dual-booting your computer with linux and windows for a while, to get the hang of linux. There are a plethora of guides available on the subject, and that way you'll never be boned without a computer if linux is acting strangely.

--T

Thank you sir, this was the exact info i was looking for . freakin 1 million reward points to you man thankies.

---

