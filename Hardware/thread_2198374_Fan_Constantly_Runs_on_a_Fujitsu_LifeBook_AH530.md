---
title: "Fan Constantly Runs on a Fujitsu LifeBook AH530"
date: 2014-01-08
forum: Hardware
---

### Post by Reuben_Williams on 2014-01-08
I am running Ubuntu 13.10 on my Fujitsu LifeBook AH530. The fan now constantly runs loudly.Even when I put a book under my laptop, with the fan intake and exit open and not covered, the fan still runs loudly. Any suggestions?

---

### Post by Bashing-om on 2014-01-10
Reuben_Williams; Weelll,

Might consider the risky alternative to install a different graphics driver.
or
-take this with a grain or two or three of salt -> as I have no experience with that hardware, might do this:
```

modprobe thermal; modprobe fan

```
prior to invoking this module, please do the back ground research.

[INDENT][INDENT]my little bit to help
[/INDENT][/INDENT]

---

### Post by Mark Phelps on 2014-01-11
The fan is running loudly because recent Linux kernels don't do a good job of idling the processor to let it cool down.  The only working solution is to throttle back the processor so it doesn't get so hot -- but that slows down the PC in general.  If you take the approach of manually slowing down the fan, you run the serious risk of burning out the processor.

We used to recommend installing Jupiter but it has been abandoned. You can try out tlp instead.

> sudo add-apt-repository ppa:linrunner/tlp
sudo apt-get update
sudo apt-get install tlp tlp-rdw


> sudo tlp start


---

### Post by king.of.random on 2014-01-11
It may be a dust problem. You can buy a can of compressed air from your local pc supplier and use it to blow out the dust especially from the fan intake and outlets. I did this to my daughters laptop over Christmas and was surprised how much quieter and faster it then ran.

---

