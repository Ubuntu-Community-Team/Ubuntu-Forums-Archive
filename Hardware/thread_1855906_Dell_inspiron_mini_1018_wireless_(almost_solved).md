---
title: "Dell inspiron mini 1018 wireless (almost solved)"
date: 2011-10-07
forum: Hardware
---

### Post by Karljv on 2011-10-07
Hi, I reinstalled my ubuntu 9.10 on mini 1018 and I did this fix once in the past, but i dont exactly remember what I did. So im stuck here.
 
Firstly I updated kernel
 
then
 
sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms
 
Problem is that when i do --> apt-get update I get an error
 
failed to fetch ppa.launchpad.net/.../binary-i386/packages.gz 404 not found
 
little help plz

---

### Post by Redblade20XX on 2011-10-07
The ppa you are using doesn't have a version of your wireless card complied for your buntu version. My suggestion is to update to a newer buntu version to see if your card is natively supported or update to a buntu that is compiled by the ppa for. :)

Here is the website of your ppa: [https://launchpad.net/~lexical/+archive/hwe-wireless]("https://launchpad.net/%7Elexical/+archive/hwe-wireless")

Look under the "[SIZE=1]Overview of published packages[/SIZE]" tab to see the versions available! ;-)

-Red

---

