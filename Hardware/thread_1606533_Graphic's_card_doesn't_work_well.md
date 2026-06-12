---
title: "Graphic's card doesn't work well"
date: 2010-10-26
forum: Hardware
---

### Post by conseil on 2010-10-26
[FONT=Verdana][SIZE=1]Hello everybody,

My friend installed Ubuntu. He has a problem with his monitor: it's blinking. Computer:[/SIZE][/FONT] [FONT=Verdana][SIZE=1]
[B]Intel Celeron D 3,2
radeon x1600pro
1,5 gb ram DDR2
asus p5ld2se
[/B][/SIZE][/FONT] [SIZE=1][FONT=Verdana][SIZE=1]I think it's caused by refreshing monitor rate. But he can't change it. He can't install ATI drivers, because it's written for Ubuntu 9. So maybe he should change something in xorg.cong? But I don't see that file... Must I generate that file? What should I do?

Thank you for answers.
Sorry for my english.[/SIZE][/FONT] 
[/SIZE]

---

### Post by mr clark25 on 2010-10-26
a blinking monitor? sounds like this *might* be a hardware issue.

on the other hand, it could be a problem within ubuntu.

im not the best with video issues, so lets get some information so that others can help.

what version of ubuntu is he running? from ubuntu 9.10 up, there is no xorg.conf file.

could you get the output of this command:
```

xrandr

```

---

### Post by boghadab on 2010-10-26
i had the same issue with kubuntu, but its fixed by going to additional drivers section in the start menue, in the system tab, you will find ADDITIONAL DRIVERS, check if your graphics card is enabled.

---

### Post by conseil on 2010-10-27
Thank you for answers. 
In Windows there's ok, so in my opinion it's not bad hardware. He has the newest version of Ubuntu (10.10). Unfortunately there aren't any additional drivers. We tried to download and install the drivers from the page of ATI. Too bad - not that version of Ubuntu(it's for 9, but he really need to newest version). So we'll try xrandr. If I got his results, I'll write it here.

Thanks

---

