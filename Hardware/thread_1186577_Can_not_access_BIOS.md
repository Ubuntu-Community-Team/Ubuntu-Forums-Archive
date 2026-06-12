---
title: "Can not access BIOS"
date: 2009-06-13
forum: Hardware
---

### Post by DougieFresh4U on 2009-06-13
Was given a nice old Thinkpad and the person who gave it to me 'wiped' the hard drive. I can not get it to boot from any kind of cd (win-ubuntu) All I get when trying to boot up machine is a 'little padlock' and cusor. 
The person I got it from does not remember password for bios. Please, can any one assist me in getting some where with this old lappy. It's really nice and the case with is great. Would like to put some kind of operating system on it
Thanks

---

### Post by jocko on 2009-06-13
From [lenovo's manual]("http://www-307.ibm.com/pc/support/site.wss/MIGR-64200.html") (for a bunch of thinkpads):
> [SIZE=3]How to remove the power-on password[/SIZE]
To remove a POP that you have forgotten, do the following:

*(A) If no SVP has been set:*
1. Turn off the computer.
2. Remove the battery pack.
    For how to remove the battery pack, see “1010 Battery pack” on page 58.
3. Remove the backup battery.
    For how to remove the backup battery, see “1120 Backup battery” on page 79.
4. Turn on the computer and wait until the POST ends.
    After the POST ends, the password prompt does not appear. The POP has been
    removed.
5. Reinstall the backup battery and the battery pack.

---

### Post by DougieFresh4U on 2009-06-13
> **jocko said:**
> From [lenovo's manual]("http://www-307.ibm.com/pc/support/site.wss/MIGR-64200.html") (for a bunch of thinkpads):

Thank you.
I went to the site and I think I am screwed!!!
I do not have supervisor password, there for  cannot enter bios.
Unless any one knows any 'guru' tricks
It's an older thinkpad 770x
I would really like to use it for 'Puppy Linux' or some other small distro.
Any thoughts, any one?

---

### Post by matt79 on 2009-06-13
Try going to the site about the computer and find a schematic of your mother board. You should see a jumper pin or switch that will allow you to erase the BIOS password.

---

### Post by dandnsmith on 2009-06-14
It's just possible that this is one of those old PCs which have vital info on the HDD, without which you cannot boot (as it contains stuff vital to the correct operation of the BIOS). I've been hit with this one several times.

To check this you'd need the model details, and a bit of searching.

---

### Post by jward3010 on 2009-06-14
When it comes to a laptop you will NOT find a jumper to zap the password or CMOS info. If you can dismantle the laptop (or even look in the doors on the bottom) you should find the CMOS battery - disconnect it, leave it off for a few hours, even overnight and it MAY clear the password. You've nothing to lose at this stage.

---

### Post by DougieFresh4U on 2009-06-21
> **jward3010 said:**
> When it comes to a laptop you will NOT find a jumper to zap the password or CMOS info. If you can dismantle the laptop (or even look in the doors on the bottom) you should find the CMOS battery - disconnect it, leave it off for a few hours, even overnight and it MAY clear the password. You've nothing to lose at this stage.

Thanks for that suggestion.
No luck.
Any other help, please?
I would really like to salvage this 'old relic'

---

### Post by DougieFresh4U on 2009-07-03
Any help please.

---

