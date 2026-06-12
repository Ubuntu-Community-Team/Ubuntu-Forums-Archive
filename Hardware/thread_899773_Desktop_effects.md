---
title: "Desktop effects"
date: 2008-08-24
forum: Hardware
---

### Post by jacquiew on 2008-08-24
Hi..

Im really new to Linux and Im trying to get the advanced desktop effects going.. also a bit of a computer noob so bear with me :p

So i got the compiz fusion command and typed that in and thats cool.. the normal effects like wobbly windows and stuff are working but things like paint fire etc arent. When I look in the hardware drivers nothing comes up.. I have a toshiba tecra A9 and it has a mobile Intel® Graphics Media Accelerator X3100 Card. Do I have to download a graphics card driver or something?

Also when I download things they dont open to install.. they go into the archive manager then I cant open them cos no programs come up. Its only some things though.. Like the flash player and plugins. I download them but they wont install and when I go to websites it still says you need the flash player.. or plugins missing. BUt when I went to download them again it said they are already installed. So frustrating!! Please help.

Ps: Ubuntu is dual booted with vista.

Cheers

---

### Post by Silver Streak on 2008-08-24
Execute the following in a terminal:

```
$ sudo apt-get install compizconfig-settings-manager
$ ccsm
```

This will allow you to access the Compiz control panel. Enjoy!

Also, have you installed the flashplugin-nonfree package yet? If not,

```
$ sudo apt-get install flashplugin-nonfree
```

---

### Post by jacquiew on 2008-08-24
Hmm but the strange thing is I already have access to ccsm.. Ive told it the effects i WANT it to do but it just wont do them. I thought maybe i have to download a driver?

Thanks for the flash player thing! Any idea about plugin commands?

---

### Post by jacquiew on 2008-08-24
OK Ive actually worked out which card i have etc.. 

Its Intel 965GM.. so that should be ok because it says it is supported.

Does anyone know exactly what you are supposed to do after you download IntelGfx-20080725 for linux? When I open the file its just a whole lot of random things and i dont know which one to open.. do I have to unzip or something?

---

