---
title: "Problem updating Ubuntu after install"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by markw10 on 2009-03-09
I just installed Ubuntu 8.1 on a Mac Pro using VMWare.  It prompted me that updates are due so I selected to update.  Now it's at the Update Manager showing 252 updates and all boxes such as close, check, and install updates, are all greyed out and the cursor is showing the circle that it's working on something.
I had this happen a few days ago so i rebooted.  This is the 2nd time trying this and I'm stuck at the same prompt.  I have even manually gone into the update manager and selected even to check for updates and it freezes up.  I have tried to search for a specific file and the same thing happens.
I have used previous versions of Ubuntu and never had this problem. I even went as far as doing a fresh install and had the same problem.  Any idea what's causing this and how I can get around this?  Thanks!

---

### Post by taurus on 2009-03-09
Close down update manager first.  Then, open a terminal and see what happens when you run these two commands.  Maybe there is something wrong with the network.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by markw10 on 2009-03-09
I also thought it was a network issue but am able to use Firefox to browse the web.  Could there be another network issue?

I tried sudo apt-get update and it went through a list and then at the end said "Reading package lists....done" and says it fetched 571KB

Then I tried sudo-apt-get upgrade.  It appears it went through an update process downloading files and installing.  It said generation complete at the end and then went back to a prompt.  It looks like both worked successfully.  

Why would it not work when I do it in update manager though?

---

### Post by Neo_The_User on 2009-03-09
no the command is sudo apt-get dist-upgrade,

---

### Post by markw10 on 2009-03-10
So do I type sudo apt-get update 
and then:
sudo apt-get dist-upgrade
?

---

