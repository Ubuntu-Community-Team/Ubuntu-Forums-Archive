---
title: "Strange problems with 500GB Seagate Barracude hard drive"
date: 2009-09-03
forum: Hardware
---

### Post by gerardlouw on 2009-09-03
I purchased a new hard drive a few months ago. It's a 500GB Seagate Barracuda. It worked perfectly until recently.

Now I'm getting two very strange problems:

1) Every few boots the hard drive isn't picked up. This doesn't seem to be entirely random. When the hard drive isn't picked up, it usually continues to not be picked up each time I restart. Later when I try again, it's picked up.

2) When the hard drive is picked up, it only stays accessible for a while - about half an hour or so. After this it becomes inaccessible, and trying to mount it gives the following message:

```
sudo mount /dev/sdb1 /store1 -t ext3

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

Is this a hardware issue? I had a 500GB Seagate Barracuda before this one, but it became completely inaccessible within the first few hours. I sent it back to the suppliers and they exchanged it with this one. I can't believe that I would get a faulty hard drive twice in a row?

The 400GB Seagate Barracuda that came with the PC is functioning perfectly and has never given me any problems.

Thanks in advance.

---

### Post by tgeer43 on 2009-09-03
I would tend to be leaning towards a physical connection problem. Try re-seating the connectors on both ends or replacing the cables altogether.

Also, when it's not being recognized try going into the BIOS to see if it's detected there. This will help determine whether it is an OS issue or something deeper.

tgeer

---

