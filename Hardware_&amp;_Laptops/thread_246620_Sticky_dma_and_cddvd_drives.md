---
title: "Sticky dma and cd/dvd drives"
date: 2006-08-29
forum: Hardware &amp; Laptops
---

### Post by katzman on 2006-08-29
Hi there, 
I am having trouble getting either my laptop or desktop (both with dapper) to get the dma on setting for thier optical drives.
I have it set in the....hdparm file to set them both to on along with the harddrives.
With the harddrives it works fine but the cd drives there is an issue.

When every i eject and load in a new disc it sets the dma to off again.
This is really starting to annoy me; so anyone have any suggestions?

---

### Post by John.Michael.Kane on 2006-08-29
katzman

check if the cd drive has the option enabled by doing a
```
sudo hdparm /dev/hdc
```

Edit the file /etc/hdparm.conf, and adding the following to the end of the file:

/dev/hdc {
dma = on
}

This should turn on dma each time you boot up the computer.

---

### Post by katzman on 2006-08-29
that is what i currently have ut it does not respect it on a new mount...or so i thought as i just checked it and i had two things for hda rather then for hdb....opps see if that fixes it

---

### Post by katzman on 2006-08-30
okay it it still not respecting it...whenever i put in a new disc i have to enable dma again.....anyother suggestions?

---

