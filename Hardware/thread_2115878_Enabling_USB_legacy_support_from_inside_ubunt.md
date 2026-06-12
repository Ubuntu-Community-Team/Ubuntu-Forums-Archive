---
title: "Enabling USB legacy support from inside ubunt?"
date: 2013-02-14
forum: Hardware
---

### Post by frash23 on 2013-02-14
Hello! I recently discovered a problem with my PC when installing #!, so i googled it and found that i had to disable legacy USB support in BIOS settings. I did so, and ended up with a brick.
I was not able to use any kind of USB input, like mouse, keyboard etc. My windows installation (current default boot up) was messed up, so i managed to install ubuntu via CD, as it automatically started with an interface where it worked.

I am now running ubuntu 11.10 64-bit (only CD that worked), and want to install windows again.

Is there a way i can enable legacy USB in my BIOS from inside of ubuntu?

Sorry if wrong section, really not sure where to post :S


EDIT:

I sloved it myself by simply pressing my "Clr CMOS" button at the backside of my computer.

Someone suggested pulling the CMOS battery, so if you are having this problem, try that.

---

### Post by carl4926 on 2013-02-14
> Is there a way i can enable legacy USB in my BIOS from inside of ubuntu?
No

BIOS settings are changed via the BIOS

---

### Post by frash23 on 2013-02-14
> **carl4926 said:**
> No

BIOS settings are changed via the BIOS

If you read my post, i accidentally disabled it, and all the forms of control i have are not working. I can't even enter the BIOS menu.

---

### Post by carl4926 on 2013-02-14
> **frash23 said:**
> If you read my post, i accidentally disabled it, and all the forms of control i have are not working. I can't even enter the BIOS menu.

You should still be able to access the BIOS or is it that your keyboard is not working at boot either?

Can you borrow a ps2 keyboard or pull the cmos battery? That may reset the BIOS

---

### Post by frash23 on 2013-02-14
> **carl4926 said:**
> You should still be able to access the BIOS or is it that your keyboard is not working at boot either?

Can you borrow a ps2 keyboard or pull the cmos battery? That may reset the BIOS

Actually, i just r ealised i had a "Clr CMOS" button at the backside of mycomputer #-o

I'll mark as solved now.

---

