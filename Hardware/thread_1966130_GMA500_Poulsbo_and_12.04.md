---
title: "GMA500 Poulsbo and 12.04"
date: 2012-04-26
forum: Hardware
---

### Post by fjgaude on 2012-04-26
Just installed 12.04 on my Dell mini-10n. Everything works as it is said to using link:

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)

That is the wonderful news! No joy with the Resume coming out of Suspend. 

Anyone working to improve the situation, Luca, Tista, anyone?

Thanks!

---

### Post by ahallubuntu on 2012-04-26
Time to sell your Dell.  I think it's long past time to sell my Acer with the same chipset.  11.04 works pretty well on it - I can even suspend and resume successfully about 9/10 of the time, but that 10th time, resume freezes and I have to do a hard reset.  I hate hard resets.

I'm looking for a faster netbook anyway.  My Acer has served its purpose well as a small travel laptop, but I would like a faster one now, please - one that plays better with Linux!

---

### Post by fjgaude on 2012-04-28
My netbook is fast enough and with 12.04 it is great for what I use it for. I just would like it to Resume after Suspend. I'll come as someone figures out what the workaround is. <smile>

---

### Post by fjgaude on 2012-05-04
My resume issue is fixed... because of an apparent typo in the suggested link:

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo/)

Under SUSPEND make sure of the double hyphen in the added text to the create file:

```
gksu gedit /etc/pm/config.d/gma500
```

Add in the following code and save the file:

```
ADD_PARAMETERS='--quirk-vbemode-restore'
```

The site shows the hyphens in front of "quirk" as one, but it should be two hyphens.

---

