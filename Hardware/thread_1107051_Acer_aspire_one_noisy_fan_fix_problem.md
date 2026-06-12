---
title: "Acer aspire one noisy fan fix problem"
date: 2009-03-26
forum: Hardware
---

### Post by rubberglover on 2009-03-26
I have posted this to the easy peasy forums but the community here is far more active so I thought I'd give you lovely knowledgeable people a try :)

I don't know much about linux - I am still learning! I am running Easy Peasy Ubuntu on an acer aspire one (8.9" screen, 160GBHD, 1GB Ram, 1.6 Intel Atom)...

I'm trying to fix the noisy fan problem... I read on the ubuntu community documentation for the aspire one that the acerfand script can cause problems and lock ups (go to [https://help.ubuntu.com/community/AspireOne]("https://help.ubuntu.com/community/AspireOne") and look under NOISE). As a result I've been trying to install the acerhdf kernel module ([http://piie.net/index.php?section=acerhdf]("http://piie.net/index.php?section=acerhdf")) and following the installation instructions on the ubuntu community documentation page i mentioned above. Works up until I get to the 'make' line in terminal, then i get this error:


[HTML]make -C /lib/modules/2.6.27-8-eeepc/build   SUBDURS=/home/andy/acerhdf_kmod modules
make: *** /lib/modules/2.6.27-8-eeepc/build: No such file or directory. Stop.
make: *** [default] Error 2[/HTML]

I'm used to using mac OSX so I'm still learning with Linux, and I don't really know what this error means so wouldn't have a clue where to start... will this module actually even work with easy peasy? Any ideas?!? :confused:

---

### Post by rubberglover on 2009-03-26
bump... (sorry - this one is just bugging me and it's probably a BASIC fix)

---

### Post by teaker1s on 2009-04-05
although I have personally had no issue's with acerfand, you would be better updating the bios as it cures noisy fan etc.
You may want to check out[ www.aspireoneuser.com]("www.aspireoneuser.com")

---

