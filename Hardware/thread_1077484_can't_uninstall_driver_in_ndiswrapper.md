---
title: "can't uninstall driver in ndiswrapper"
date: 2009-02-22
forum: Hardware
---

### Post by Meados on 2009-02-22
I am trying to uninstall a driver in ndiswrapper that is not a valid driver but I can't.. I always get this error:

> home@home-laptop:~$ ndiswrapper -e synpd
couldn't delete /etc/ndiswrapper/synpd: esse ioctl não é apropriado para o dispositivo


I also tried with -r.

This was an mouse driver for notebook.. May this program just work for network drivers?

How can I uninstall it then? :S

---

### Post by cariboo on 2009-02-22
Ndiswrapper is only a wrapper for network device drivers. You can use System-->Administration-->Synaptic Package Manager to completely remove ndiswrapper.

Jim

---

### Post by Meados on 2009-02-22
> **cariboo907 said:**
> Ndiswrapper is only a wrapper for network device drivers. You can use System-->Administration-->Synaptic Package Manager to completely remove ndiswrapper.

Jim

Ok, I didn't know. But I don't want to remove it completely, just the invalid drivers that I installed in it.

Thanks.

---

### Post by Meados on 2009-02-23
> **Meados said:**
> Ok, I didn't know. But I don't want to remove it completely, just the invalid drivers that I installed in it.

Thanks.

So any idea how to remove the invalid drivers?

---

### Post by caljohnsmith on 2009-02-23
It looks like you forgot to run the ndiswrapper command as root, so how about trying:
```
[COLOR="Blue"]sudo[/COLOR] ndiswrapper -r synpd
```

---

### Post by stchman on 2009-02-23
Install the ndisgtk package.

```
sudo apt-get install ndisgtk
```

Much better than editing text files.

---

### Post by Meados on 2009-02-23
> **caljohnsmith said:**
> It looks like you forgot to run the ndiswrapper command as root, so how about trying:
```
[COLOR="Blue"]sudo[/COLOR] ndiswrapper -r synpd
```

Yup.. I forgot sudo. :p

I deleted them now. Thanks!

> Much better than editing text files. 

hmm... I didn't edit any text file, I just executed codes of ndiswrapper at terminal.

That is just a «graphical» ndiswrapper?

---

### Post by stchman on 2009-02-24
> **Meados said:**
> Yup.. I forgot sudo. :p

I deleted them now. Thanks!



hmm... I didn't edit any text file, I just executed codes of ndiswrapper at terminal.

That is just a «graphical» ndiswrapper?

Yes.

---

