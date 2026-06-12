---
title: "Freecom Network Drive mounting problems"
date: 2009-03-02
forum: Hardware
---

### Post by GapInTheClouds on 2009-03-02
Hi,

I've just got a 500GB Freecom Network Drive, which I can connect to via a wireless router on Windows without a problem. In Ubuntu its been a bit more difficult. You can see the drive in the following, but it has weird symbols in it:

```

hugo@crazy-mac:~$ findsmb

                                *=DMB
                                +=LMB
IP ADDR         NETBIOS NAME     WORKGROUP/OS/VERSION 
---------------------------------------------------------------------
192.168.1.65    CRAZY-MAC     +[WORKGROUP] [Unix] [Samba 3.2.3]
192.168.1.66    FND            [&#519;] [] [&#65533;&#65533;&#65533;]
hugo@crazy-mac:~$ 

```

When I try and mount the drive it seems to bring up a window that almost immediately disappears again. If I use the File Browser to look at 'Windows Network' I can see FND and its shares, but as soon as I click on the share, it quickly reverts back to my home directory.

Any ideas? Any help greatly appreciated.

---

