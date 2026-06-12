---
title: "Wireless quit working after updates after fresh instal of Intrepid"
date: 2009-01-07
forum: Hardware
---

### Post by Sanketsu on 2009-01-07
Ok, so I've got a Sony Vaio PCG-V505BX and due to a recent hard drive failure decided to put Intrepid on it since prior I had Hardy.  I installed the new hard drive with no issues and promptly did a full drive install of Ubuntu.  After that, it connected to my wireless network with no problems just as it had with Hardy, however there were 200+ updates that it had available, I took a quick scan through the list and figured I'd just let the whole lot update, and did.  After that the system required a restart, I'd assume from the Linux-image (kernel?) update.  Everything seemed to go just fine up until the system tried to reconnect to my wireless network.  The swirl went almost instantly to both orbs going green and then just hanging there until I get "The network connection has been disconnected".

After looking at some things I found this thread:

[http://ubuntuforums.org/showthread.php?t=393892](http://ubuntuforums.org/showthread.php?t=393892)

And followed the advice in the second post to get:

```
02:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
```

Then from there I entered the
```
lspci -v | grep -i Network
```
and got nothing at all back.

Now I'm lost.  Any help would be greatly appreciated.

-=edit=-
I've just now tried to connecting my laptop to the internet via a wired Ethernet connection and am getting the same issue.

---

### Post by Sanketsu on 2009-01-07
Anyone have any suggestions at all?

---

### Post by kozhi on 2009-01-21
The problem below was solved, thanks to another post that I located at [http://ubuntuforums.org/showpost.php?p=6165899&postcount=19](http://ubuntuforums.org/showpost.php?p=6165899&postcount=19)

Sanketsu: > "Anyone have any suggestions at all?

" I have exactly the same problem (except for the card, which happens to be Ath) - wireless stops after installing updates - and came upon your posts, landed up at the thread you mentioned, and from there, went to another (a detailed post by webdr): [HTML]http://ubuntuforums.org/showthread.php?t=420627&highlight=madwifi[/HTML]

Must confess, I can't make much of it, being quite new to linux.

I had initially installed the madwifi driver for the atheros card following instructions on one of the forums (quite detailed instructions by reasoner), and it worked really well. Now when I do "```
lsmod | grep  ath
```" I get: ath_pci, wlan, ath_hal listed

So not sure if need to blacklist one of the aths, if so which one, or if there is some easier way than the one suggested in the thread mentioned above from webdr. Any suggestions would be really wonderful.

---

