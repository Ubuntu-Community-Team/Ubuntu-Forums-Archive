---
title: "Frustrating Samba issue"
date: 2009-06-05
forum: Installation &amp; Upgrades
---

### Post by kamasabi on 2009-06-05
hey ya'll,

I've come across an issue I'm having with my samba configuration and was hoping someone here could help.  When I log in from my windows machine, and I drop a file somewhere, someone on a separate account (I have my account and a guests account set up), the guests account does not have access to read something that I had dropped in on my account.  Anyone know why this might be happening?  What I would like to happen is when something is dropped within one of these shares (whether it be I or the guest account that drops it in), I want everyone to have read access to it.  I mean, a simple

sudo chmod -R 777 /netshare/***foldername here***

fixes the issue, however, I would like it to be like this for every file dropped in any of those shared directories.

Here is a copy of the permissions within my smb.conf:

```
[Public Share]
comment = Put yer stuff here
path = /netstorage/Publicshare
browseable = yes
read only = no
writeable = yes
valid users = kamasabi, guests
admin users = kamasabi
create mask = 0600
directory mask = 0700

[Video]
path = /netstorage/Video
browseable = yes
read only = yes
valid users = kamasabi, guests
write list = kamasabi
create mask = 0600
directory mask = 0700

[Music]
path = /netstorage/Music
browseable = yes
read only = yes
valid users = kamasabi, guests
write list = kamasabi
create mask = 0600
directory mask = 0700

[Programs]
path = /netstorage/Programs
browseable = yes
read only = yes
valid users = kamasabi, guests
write list = kamasabi
create mask = 0600
directory mask = 0700

[Operating Systems]
path = /netstorage/OS
browseable = yes
read only = yes
valid users = kamasabi, guests
write list = kamasabi
create mask = 0600
directory mask = 0700

[Kamasabi's Stuff]
path = /netstorage/Kamasabi
browseable = yes
read only = no
valid users = kamasabi
create mask = 0600
directory mask = 0700

[Games]
path = /netstorage/Games
browseable = yes
read only = yes
valid users = kamasabi, guests
write list = kamasabi
create mask = 0600
directory mask = 0700

```

---

### Post by kamasabi on 2009-06-06
disregard, I feel like an idiot after I looked back at the masks :p

---

