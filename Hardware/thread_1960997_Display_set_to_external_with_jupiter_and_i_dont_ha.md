---
title: "Display set to external with jupiter and i dont have an external display"
date: 2012-04-18
forum: Hardware
---

### Post by mzunguInKenya on 2012-04-18
So i admit it im still a noob. iv been playing with ubuntu for a little under a year, and i just joined this forum a few months ago so this is my first post. and i appologize if its already been addressed because i didnt see it posted anywhere

 i just installed jupiter and accidentally switched the option to external screen, this would be no problem if i had one to connect to switch it back but i dont.  i can log into the guest account and it still uses the laptop screen which i am thankful for so if anyone could help me out i cant seem to find any support for jupiter by google search.

much thanks for anyone willing to spend a few min to walk me through this stupid mistake

---

### Post by mzunguInKenya on 2012-04-18
[SIZE=3]any ideas? anyone! suggestions please im desperate [/SIZE]

---

### Post by mzunguInKenya on 2012-04-18
just wanted to thank everyone for their help! i just removed jupiter from my guest account and then when i logged into the regular account the screen was back to the way it should be!:guitar:

---

### Post by mzunguInKenya on 2012-04-19
<deleted>

---

### Post by dunbrokin on 2012-05-20
I have the same problem...I often forget to switch from external screen to internal screen when I take my laptop away..and can only use the guest account. It would really be great if somebody could help and write a script which would test whether there is a external screen attached on boot up...and if there is not then default to internal screen and thus overwrite the Jupiter choice

---

### Post by compNk on 2012-06-30
Got the same issue but found a way rather than remove Jupiter,

Simply delete the file 'vga_saved' under '/var/jupiter'.

Could done by

> rm /var/jupiter/vga_saved

---

### Post by dunbrokin on 2012-06-30
Good in theory...but you cannot see anything on the screen in your normal profile and the guest profile will not allow you access to the command line.

---

