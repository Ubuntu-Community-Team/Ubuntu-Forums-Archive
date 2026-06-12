---
title: "wireless wep"
date: 2008-07-21
forum: General Help
---

### Post by SpenceMakesSense on 2008-07-21
When I try to enter my wep key to use my wifi it doesnt connect and then asks as if i had the wrong key. I have a dell inspiron 1521 and im not sure what internal wireless card it has but i installed it with ndiswrapper because ndisgtk wouldnt install it correctly.

---

### Post by Potatoj316 on 2008-07-21
What is your encrytption strentgh, 128 or 64 bit.  You might have to tell it which you use, it might not autodetect correctly.

---

### Post by SpenceMakesSense on 2008-07-21
it will only actually let me enter it with one kind which is the 128 default one. and ive gotten it to work with my other boxes on the same code and settings

---

### Post by Potatoj316 on 2008-07-21
Where they using Ubuntu as well or was it Windows or another linux distro?

---

### Post by SpenceMakesSense on 2008-07-21
ubuntu, but it does in fact work on windows too

---

### Post by Potatoj316 on 2008-07-21
Are they all the same versions of ubuntu, if not what are they and which is the one that isnt working

---

### Post by SpenceMakesSense on 2008-07-21
all ubuntus are 8.04 including the one im using

---

### Post by Potatoj316 on 2008-07-21
Do they have different wireless cards, are they desktops or laptops and make sure to designate which is the problematic one

---

### Post by SpenceMakesSense on 2008-07-21
my dell inspiron laptop is the only one having problems connecting, and they all have different wireless cards/usb adapters. i have 2 boxes using ubuntu with working wireless once using linksys wireless n andmy other box using linksys wireless g. which ubuntu has driveres for the g while i must use indiswrapper to install n. I have no cluue what my laptop has  just know what kind of laptop it is.

---

### Post by Potatoj316 on 2008-07-21
Try looking in the restricted drivers manager (System->Administration) Your wireless card might be there.

---

### Post by hal8000 on 2008-07-21
> **SpenceMakesSense said:**
> When I try to enter my wep key to use my wifi it doesnt connect and then asks as if i had the wrong key. I have a dell inspiron 1521 and im not sure what internal wireless card it has but i installed it with ndiswrapper because ndisgtk wouldnt install it correctly.


You must know what make/model your wireless adapter is otherwise how would you know which windows driver to load??

Post the output of

sudo ndiswrapper -l

Your laptop uses a broadcom chipset so should work with the windows drivers using ndiswrapper

Thers a guide for the Inspiton 1501
[http://www.ubuntu1501.com/2007/11/wireless-in-gutsy-gibbon-with.html](http://www.ubuntu1501.com/2007/11/wireless-in-gutsy-gibbon-with.html)


One basic check to try. Temporary turn off the encrption on your wireless network, this way you can test that you have your wireless card working, then turn on your encrption

---

### Post by SpenceMakesSense on 2008-07-21
no its not there just  my graphics

---

### Post by SpenceMakesSense on 2008-07-22
I went to my other pcs and discovered this is happening with all my ubuntu/xubuntu boxes but not my windows xp boxes. My main pc has a linksys wireless n usb adapter. It has worked before. so now this seems to big a larger dilemma then i thought

EDIT: Actually theyre working with my windows xp which are dual booted with the ubuntu/xubuntu boxes so theyre using the same wireless receivers

---

