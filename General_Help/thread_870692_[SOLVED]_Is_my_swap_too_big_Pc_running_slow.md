---
title: "[SOLVED] Is my swap too big? Pc running slow"
date: 2008-07-26
forum: General Help
---

### Post by Drizzel on 2008-07-26
I recently did a clean install of Ubuntu and chose to make my swap bigger than before. I have 256mb on this pc and before I always let the partitioner do auto config on the swap during the install. It was 667mb before.. This time I made it 1gb. There seems to be a lot of hdd activity going on while doing minor tasks. Things that opened fast before take longer now. Did I make the swap too big? I have gparted should I resize? I dont know what else could be causing the slowness.

---

### Post by sdennie on 2008-07-26
It's probably not too big, no.  With 256M of RAM, you can expect a lot of swap activity and that will generally slow your machine.  If at all possible, I would try to upgrade to at least 512M of RAM.  Changing the swappiness value may help as well.  Edit /etc/sysctl.conf and add the following line:

```

vm.swappiness = 0

```

Then run:

```

sudo sysctl -p

```

That should make the machine prefer RAM to swap and will insure that it stays that way every time you reboot.

---

### Post by Drizzel on 2008-07-26
Yeah I need to get some more ram.. Thx for the reply. :)

---

### Post by ryank76nz on 2008-08-28
OMG that worked awesomely for me. Thanks!!!!

---

