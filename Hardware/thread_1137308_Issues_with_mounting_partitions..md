---
title: "Issues with mounting partitions."
date: 2009-04-25
forum: Hardware
---

### Post by And1945 on 2009-04-25
Hi,

I could not really find anything relevant, so I thought I would just ask, since this is bothering me a great deal.

I have dual boot. Actually just because my daily work is in Adobe applications... nevermind that.

I have a partition table like this:
windows 40gb
ubuntu 9.04 root 40gb
swap 2gb
home part 40gb
EMPTY? 100gb ~
windows recovery (bundled from hp)

My problem now, lay with the fact that I can not mount "empty" which I have tried during install, and afterwards with gpart, to make a viable partition. No matter what I do, it does not look like it is going to budge.

If I click on the permissions tab in preferences it tells me that it can not aquire partition permissions.

What have I done wrong?

Thanks in advance,
The frustrated dane.

---

### Post by And1945 on 2009-04-25
Nevermind,

I found the problem. Per default, the user you create during 9.04 install, does not have permissions to mount drives, that isnt directly affiliated with your user. You have to change that in system -> administration -> users and groups. Unlock it, and voila.

---

