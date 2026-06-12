---
title: "How to install netboox remix with ext4"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by hesjnet on 2009-04-23
How do I install Ubuntu Jaunty Jackalope 9.04 Netbook Remix with the new filesystem EXT4? I cannot locate an alternative image for this version..

---

### Post by hesjnet on 2009-04-23
And also: Is ext4 faster on SSD drives?

---

### Post by AK Dave on 2009-04-23
Jaunty itself is overall much faster than Intrepid or Hardy, especially on boot. I don't know how much of that additional speed or crispness is ext4, but thats what I have.

My install was created on my Dell Mini-9 using the i386 desktop install of Jaunty, and then this command:
```
sudo apt-get install ubuntu-netbook-remix
```

---

### Post by snowpine on 2009-04-24
> **hesjnet said:**
> How do I install Ubuntu Jaunty Jackalope 9.04 Netbook Remix with the new filesystem EXT4? I cannot locate an alternative image for this version..

Use the normal installer. When you get to the Partitioning step of the install, choose Manual, and then you can use ext4.

---

