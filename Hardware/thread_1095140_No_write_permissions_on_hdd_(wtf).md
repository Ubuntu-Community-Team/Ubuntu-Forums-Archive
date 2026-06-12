---
title: "No write permissions on hdd (wtf)"
date: 2009-03-13
forum: Hardware
---

### Post by Daveyon on 2009-03-13
Hello fellow mates. Just installed the 8.10 version on my Dell Vostro 1500 lappy. Duoble clicked in my "filesyste" or hdd, open up some folders - all and I cannot create a new folder. I can't even copy n paste to my hdd. Why is that and how to solve this?

If i go to permissions tab, I get this: "The Permissions of '/' could not be determined." What is going on here?

---

### Post by taurus on 2009-03-13
Do you want to write to / (root filesystem)?  You don't have permission to write or modify anything outside your $HOME.  To do that, you need root privilege--sudo/gksudo.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Daveyon on 2009-03-13
Thanks. Im a noob so c with me lol.

---

