---
title: "USB hardisk install - automounter messing up?"
date: 2006-02-20
forum: Hardware &amp; Laptops
---

### Post by timov on 2006-02-20
Hija,

I'm trying to help a friend of mine (other side of the country to make things easy) run a Linux distro as he wants to learn how Linux works. After runnign Ubuntu for a bit myself I advised him to use this and give it a go. 

To keep things simple I suggested he use his external (80Gb) usb hard drive so he wouldn't risk his windows install (he's a compelte Linux newbie so didn't want to drop him in dual boot problems :))

The install seems to have gone fine but the system doesn't boot properly. He's on the other side of the country (as I said) so I haven't seen the problems first hand, so just relaying what I hear and assume.

Somehow the system boots, but when booted sda1 (the / partiton) has somehow been mounted on /media/sda1. Needless to say this causes shitloads of problems.

I had him boot back into windows and send me a copy of /etc so I could have a look see, but all seems fine (mtab and fstab show the correct entries for mounting /dev/sda1 on /).

I have a feeling the problem might lie in the automounter kicking in after the system boot has completed (although it baffles me how it managed to unmount /).

Anyone seen this behavior before? And if so know a solution. Or if not any docs out there on disableling the automounter so I can give that a whirl?

thanx

Timo

---

### Post by Cth on 2006-02-20
[http://www.ubuntuforums.org/showthread.php?t=80811](http://www.ubuntuforums.org/showthread.php?t=80811)

I just did a Ext USB hard drive. I would have your friend start reading from page 1 to the end. It took me 3 0r 4 time to get it going. But it works.

Chris.

---

