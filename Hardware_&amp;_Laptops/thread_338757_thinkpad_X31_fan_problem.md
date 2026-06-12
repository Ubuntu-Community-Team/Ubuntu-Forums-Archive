---
title: "thinkpad X31 fan problem"
date: 2007-01-14
forum: Hardware &amp; Laptops
---

### Post by lenso on 2007-01-14
I'm new to using Ubuntu (Edgy) and noticed that after a week of using it for several hours, my temperatures start at 34C to 55C and the fan never turns on. I searched here and thinkwiki about fancontrol and tried using the ibm-acpi method but it was unsuccessful. I kept getting permission denied whenever trying to write to the register. Anyone successful with getting to the fan on the x31 to start spinning? I love using Ubuntu rather than Windows but if its the life of my processor on the line, I would be forced to go Windows.

---

### Post by lenso on 2007-01-15
bump...

---

### Post by ubuntu.daemon on 2007-02-24
i have the same issue, as well as the fact that i am trying to find how to customize xubuntu a lil more.  I want to see how much battery power i have left, wireless ima try tomorrow, i dont know if my card will support wpa, i have the cxu model.  Hit me back.

---

### Post by Ptero-4 on 2007-02-24
The fan problem might be that the fan is stuck in dust, get a can of compresed air, open the laptop and direct it at the inside of the laptop.

---

### Post by twoblackeyes on 2007-03-09
Download the tp-fancontrol script here: [http://www.thinkwiki.org/wiki/ACPI_fan_control_script#Variable_speed_control_scripts](http://www.thinkwiki.org/wiki/ACPI_fan_control_script#Variable_speed_control_scripts)

Save it to a directory and then in a terminal, after navigating to that directory, type:

```
sudo ./tp-fancontrol -d
```

Your fan should kick on automatically if things start to get too hot. You can monitor it with the default gnome sensor applet for the title bar. 

You can also add this command to your startup script to make this happen automatically. There's more info on that @ thinkwiki.

---

### Post by ubuntu.daemon on 2007-03-10
wootskies thank you!

you just forgot to mention the part to make both those scripts executable...

chmod 750

AND you need to add it to the startup sequence, so you're not doing it everytime you log on.

sudo update-rc.d tp-fancontrol defaults

YAY so COOL!:lolflag:

---

### Post by bronevaya on 2007-05-08
sorry to dig up, but does feisty take care of the heat/fan problem automatically? if not then i dont want to be installing an os on my laptop that can potentially damage it

---

### Post by ubuntu.daemon on 2007-05-08
lol no not off the bat, but if you read my posts as well as the others it isnt too hard.  Its not all laptops that do this just some unsupported ones.  If you need some help let me know and ill be happy to help.

---

### Post by Rogbert on 2008-04-10
Can you break that down for a new linux user?  I'm using an x31 with gutsy and have had the same fan problems.  Worried it'll damage my machine.  How do I point my browser to the package?  I need to know the exact commands to run this if you don't mind.
Thanks!

---

