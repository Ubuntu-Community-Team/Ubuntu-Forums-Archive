---
title: "LiveUSB. AlpsPS/2 Touchpad"
date: 2015-09-25
forum: Hardware
---

### Post by abrahamdel91 on 2015-09-25
Hi, everyone.

I'm trying out 64-bit Ubuntu_MATE 15.04 from an USB on my eMachines eM350 netbook, and it doesn't mounts the touchpad... it also happened few weeks ago with Lubuntu; later when I installed the OS, it worked so I didn't pay much attention (It didn't happen at all with Ubuntu or Xubuntu). This time I'm not willing to install, but I would love to make it work.

I got this on Terminal:

```
[FONT=courier new]ubuntu-mate@ubuntu-mate:~/Desktop$ xinput
&#9121; Virtual core pointer                         id=2   [master pointer   (3)] 
&#9116;     &#8627; Virtual core XTEST pointer            id=4   [slave  pointer   (2)]
&#9123; Virtual core keyboard                        id=3   [master keyboard  (2)]
     &#8627; Virtual core XTEST keyboard             id=5   [slave  keyboard  (3)]
     &#8627; Power Button                            id=6   [slave  keyboard  (3)] 
     &#8627; Video Bus                               id=7   [slave  keyboard  (3)]     
     &#8627; Power Button                            id=8   [slave  keyboard  (3)]     
     &#8627; Sleep Button                            id=9   [slave  keyboard  (3)] 
     &#8627; WebCam                                  id=10  [slave  keyboard  (3)]
     &#8627; AT Translated Set 2 keyboard            id=11  [slave  keyboard  (3)] 
     &#8627; Acer WHI hotkeys                        id=12  [slave  keyboard  (3)][/FONT]
```

As you can see, there is not listed the touchpad. On the other hand, when I use 'xinput' on my Xubuntu current installation it returns the following results:

```
[FONT=courier new]abraham@abraham-xub:~$ xinput
&#9121; Virtual core pointer                          id=2   [master pointer   (3)] 
&#9116;     &#8627; Virtual core XTEST pointer             id=4   [slave  pointer    (2)]
[FONT=courier new]&#9116;     &#8627; **AlpsPS/2 ALPS GlidePoint**               id=12  [slave  pointer    (2)]
[FONT=courier new][FONT=courier new]&#9116;     &#8627; **Alps PS/2 Device **                       id=13  [slave  pointer    (2)][/FONT][/FONT][/FONT]
&#9123; Virtual core keyboard                         id=3   [master keyboard  (2)]
     &#8627; Virtual core XTEST keyboard              id=5   [slave  keyboard  (3)]
     &#8627; Power Button                             id=6   [slave  keyboard  (3)] 
     &#8627; Video Bus                                id=7   [slave  keyboard  (3)]     
     &#8627; Power Button                             id=8   [slave  keyboard  (3)]     
     &#8627; Sleep Button                             id=9   [slave  keyboard  (3)] 
     &#8627; WebCam                                   id=10  [slave  keyboard  (3)]
     &#8627; AT Translated Set 2 keyboard             id=11  [slave  keyboard  (3)] 
     &#8627; Acer WHI hotkeys                         id=14  [slave  keyboard  (3)][/FONT]
```

Then, what do you think may be the cause? And how could it be fixed?

Thanks in advance,

Abraham Medina.

---

