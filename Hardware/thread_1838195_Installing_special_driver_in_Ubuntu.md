---
title: "Installing special driver in Ubuntu"
date: 2011-09-03
forum: Hardware
---

### Post by tontis on 2011-09-03
Hello,
I'm new to Linux and Ubuntu and i'd like some help installing a driver for an external sound card i've got from Line6 a few years ago.

I found this [_webpage_]("www.tanzband-scream.at/live6") where somebody developed a linux compatible driver (as far as I see supposedly including Ubuntu). [www.tanzband-scream.at/live6](www.tanzband-scream.at/live6)

However I was reading the installing instructions and have been at it for a while with no success.
Firstly I tried using the .rpm intallation. After a while I realized it was no good(for red hat obviously hehe..) I tried converting the .rpm file into a .deb with Alien. It didn't work, said it was for amd64 system. I believe I have amd64.

Anyway I started trying to installing it directly with the source files, also from the webpage.

I tried the instructions from the web page - no good.
"tar xjf line6usb-0.8.1.tar.bz2
cd line6usb-0.8.1
make install"

So then I was trying to understand how to make a .deb file from the extracted source files, yet it just made my head spin... Anybody could help me please?

Thanks in advance.

---

### Post by sanderd17 on 2011-09-03
The link doesn't work, please correct it.

And: when you try to build it from source, give us the output of the terminal. That way we can see where it goes wrong.

PS. Post anything code-related between CODE tags (click on the #-symbol).

---

### Post by tontis on 2011-09-04
> The link doesn't work, please correct it.

I've tried, doesnt work. But, if you copy and paste the url into a new window it does. [http://www.tanzband-scream.at/line6/](http://www.tanzband-scream.at/line6/)


> And: when you try to build it from source, give us the output of the terminal. That way we can see where it goes wrong.

The code output:

```
agne@Bixo:~$ tar xjf /home/agne/line6usb-0.8.1.tar.bz2
agne@Bixo:~$ cd /home/agne/line6usb-0.8.1
agne@Bixo:~/line6usb-0.8.1$ make install
./set_revision.sh
make -f Makefile -C /lib/modules/2.6.38-11-generic/build CONFIG_LINE6_USB=m SUBDIRS=/home/agne/line6usb-0.8.1 modules
make[1]: Går till katalogen "/usr/src/linux-headers-2.6.38-11-generic"
  CC [M]  /home/agne/line6usb-0.8.1/audio.o
/home/agne/line6usb-0.8.1/audio.c: In function ‘line6_init_audio’:
/home/agne/line6usb-0.8.1/audio.c:31:2: error: implicit declaration of function ‘snd_card_new’
/home/agne/line6usb-0.8.1/audio.c:31:7: warning: assignment makes pointer from integer without a cast
make[2]: *** [/home/agne/line6usb-0.8.1/audio.o] Fel 1
make[1]: *** [_module_/home/agne/line6usb-0.8.1] Fel 2
make[1]: Lämnar katalogen "/usr/src/linux-headers-2.6.38-11-generic"
make: *** [default] Fel 2

```

fel simply means error. sorry its in swedish.

Also, since last time I was poking around, probably with things I shouldnt have, I had trouble booting. It just got to one point where it didn't move. It didn't freeze, just didn't continue the booting process. I had this problem before aswell, but it usually worked after shutting down and trying again. Should I be worried?

---

### Post by sanderd17 on 2011-09-04
experimantal software, last updated in 2009. That normally means it's broken. Sorry, you'll have to search something else.

Are you able to boot now?

If not, when you boot and you see the GRUB screen (where you can select your OS). Het 'E' to edit the line. Delete the words "quiet splash" and hit CTRL+X to boot. This will show you text output instead of a splash screen, so you can see where it hangs.

Don't be afraid do edit something wrong. It's only a temporal setting (it will last one boot cycle).

---

### Post by tontis on 2011-09-04
I can boot, but i'll try your advice anyway, wanna make sure nothing is wrong.

Well, thanks for your time! I'll keep searching and if I find something i'll keep you updated

---

