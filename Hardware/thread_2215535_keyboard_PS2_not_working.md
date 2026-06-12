---
title: "keyboard PS2 not working"
date: 2014-04-07
forum: Hardware
---

### Post by jhay2 on 2014-04-07
hi im using lubuntu 13.10 

my problem is that PS2 keyboard does'nt work on my lubuntu OS .

when i plug the keyboard , numlock ,capslock and Scroll lock lights on and then it turns off after 1 second

my PS2 mouse are working . only PS2 keyboard does not work on my device.. 

How would i get this keyboard works :( i already googled this issue but no solution found, 

please help  


sorry for my bad english 


any replies are much appreciated

---

### Post by Bashing-om on 2014-04-07
jhay2; Hi !

1st, check in your bios setup and see if there is not an option for "legacy" for the keyboard.
Else --- there "might" be something that can be done in grub to get the system to recognize the ps-2 keyboard.

FYI I do use a ps2 keyboard with 'buntu 13.10 (AMD desktop) with no problem.

[INDENT][INDENT]maybe yes,
[INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jhay2 on 2014-04-08
> **Bashing-om said:**
> jhay2; Hi !



hello , thanks for your reply 

> 

1st, check in your bios setup and see if there is not an option for "legacy" for the keyboard.


I dont have that kind of option on my bios .. 

before im using windows , PS2 keyboard works without entering on my bios setup 

but here at linux i tried also MInt , but no luck PS2 keyboard doesnt work . only PS2 mouse is working

> 


Else --- there "might" be something that can be done in grub to get the system to recognize the ps-2 keyboard.


what should i do with the grub config to be able to detect my ps2 keyboard ? 


> 


FYI I do use a ps2 keyboard with 'buntu 13.10 (AMD desktop) with no problem.[INDENT][INDENT]maybe yes,[INDENT][INDENT]maybe not so yes
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


yes , i 'd read at google that PS2 work on ubuntu .. but there were some user that are unlucky to make PS2 works on ubuntu, including me.. :( just like what you've said , i think there might be something to be done at my grub config . but i dont know what should i do with the  grub config to make PS2 keyboard work ..

---

### Post by Bashing-om on 2014-04-08
jhay2; Humm, well

We can take a gentle poke at it, and see what results:
Make an edit to the "/etc/default/grub" file:
Make a backup 1st as Standard Operating Procedure:
```

sudo cp /etc/default/grub /etc/default/grub-08apr2014

```
Now edit the file:
```

gksudo gedit /etc/default/grub

```(gksudo is the graphical equivalent of 'sudo' to attain elevated privileges  )
find this line: -> " #GRUB_TERMINAL=console "
and remove the '#' symbol at the start of the line such then that the line gets parsed.
save the file and exit back to terminal:
Propagate the change by terminal code:
```

sudo update-grub

```
Reboot and let's see what the effect is.

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jhay2 on 2014-04-09
It only gives me a large font size at grub boot 

But other than that no effects at all .. :(

---

### Post by Bashing-om on 2014-04-09
jhay2; UnGood !

To me that indicates that grub can not find a driver for the ps/2 keyboard.

 It is beyond my knowledge as to how to load a driver for grub if bios can not pass that information onto the booting stage. One of these days I might be that well informed, but it ain't now.

Perhaps others can advise better.

As you probably are aware, you might try a ps2/usb adapter and see if a usb port will pick up the keyboard.
Else looking at biting the bullet and using a usb keyboard.

May as well revert that change in '/etc/default/grub' as it did not have the desired effect.

? this one of those times
[INDENT][INDENT]there just is not a good solution
[/INDENT][/INDENT]

---

### Post by jhay2 on 2014-04-11
ouch. :( 

By the way thanks for trying to help i really appreciate it 



Hope someone can help me with this problem

---

