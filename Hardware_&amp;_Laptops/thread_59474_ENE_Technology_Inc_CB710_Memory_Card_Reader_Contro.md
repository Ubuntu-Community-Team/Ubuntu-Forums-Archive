---
title: "ENE Technology Inc CB710 Memory Card Reader Controller"
date: 2005-08-24
forum: Hardware &amp; Laptops
---

### Post by foxy123 on 2005-08-24
I've got the aforementioned device on my NEC Versa M400 laptop and it does not seem to work. It shows in lspci:
```
0000:01:04.0 CardBus bridge: ENE Technology Inc CB710 Cardbus Controller (rev 01)
0000:01:04.1 FLASH memory: ENE Technology Inc CB710 Memory Card Reader Controller
``` 
but if I insert a card, nothing happens. Has anyone have luck with making it work?

---

### Post by crapufish on 2006-05-28
Hello!

I have the same problem and I searched these forums over and over again... 

Please Help!!!


I am using Ubuntu Dapper and the lspci output looks like this:
```

0000:02:01.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller (rev 02)
0000:02:01.1 FLASH memory: ENE Technology Inc CB710 Memory Card Reader Controller
```

The problem is that when I input a card, nothing seems to happen (dmesg doesn't output nothing when I insert the card).


Thanks a lot!

](*,)


[QUOTE=foxy123]I've got the aforementioned device on my NEC Versa M400 laptop and it does not seem to work. It shows in lspci:
```
0000:01:04.0 CardBus bridge: ENE Technology Inc CB710 Cardbus Controller (rev 01)
0000:01:04.1 FLASH memory: ENE Technology Inc CB710 Memory Card Reader Controller
``` 
but if I insert a card, nothing happens. Has anyone have luck with making it work?[/QUOTE]

---

### Post by foxy123 on 2006-05-29
[QUOTE=crapufish]Hello!

I have the same problem and I searched these forums over and over again... 

Please Help!!!


I am using Ubuntu Dapper and the lspci output looks like this:
```

0000:02:01.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller (rev 02)
0000:02:01.1 FLASH memory: ENE Technology Inc CB710 Memory Card Reader Controller
```

The problem is that when I input a card, nothing seems to happen (dmesg doesn't output nothing when I insert the card).


Thanks a lot!

](*,)[/QUOTE]
as far as I know it is not supported... at least I have not found anything on the net about it...

---

### Post by crapufish on 2006-05-29
[QUOTE=foxy123]as far as I know it is not supported... at least I have not found anything on the net about it...[/QUOTE]

The thing is that, as far as I understood, the new kernel 2.6.17 supports this card readers... so I think there should be a driver or something around there... I searched google, forums, you name it, but without concrete solutions. Some people reports they are using it, they can see messages in system log when they insert a card and then they can mount that card. :-k 

Any help will be greatly appreciated!

---

### Post by foxy123 on 2006-05-29
[QUOTE=crapufish]The thing is that, as far as I understood, the new kernel 2.6.17 supports this card readers... so I think there should be a driver or something around there... I searched google, forums, you name it, but without concrete solutions. Some people reports they are using it, they can see messages in system log when they insert a card and then they can mount that card. :-k 

Any help will be greatly appreciated![/QUOTE]
really? keep us posted then please...

---

### Post by dustrho on 2007-04-11
I am having the same problem with my HP Pavilion zd7020 laptop, as it also has this exact same memory card reader built-in. I would love to learn of a way to getting this thing working again.

---

### Post by davidsrsb on 2007-04-17
Under Feisty Fawn with my NEC laptop I get:
01:04.0 CardBus bridge: ENE Technology Inc CB-710/2/4 Cardbus Controller (rev 01)
01:04.1 FLASH memory: ENE Technology Inc CB710 Memory Card Reader Controller

Still not working though

---

### Post by emmerc on 2007-04-18
I am using Ubuntu 6.10 in a Toshiba Satellite Pro 6100 and everything works well but the built in SD card reader.  I have tried everything but still it does not work. If someone has any solution please help me!

With lspci and dmesg | tail I got this information: 

[17180010.552000] sd 0:0:0:0: Attached scsi removable disk sda
[17180010.572000] sd 0:0:0:0: Attached scsi generic sg0 type 0


02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)

---

### Post by HarshReality on 2007-06-24
Since this thread was started with a specific reader in mind (Yea I have this one too in my zd7010) maybe it should get a sticky or something until its resolved or worked around.

---

### Post by tonyric on 2007-06-24
I had this reader in my old HP ZD7000 laptop and it was never supported. Not sure about the newer kernels though.

---

