---
title: "Testing a hard drive for health"
date: 2013-09-23
forum: Hardware
---

### Post by rapattack on 2013-09-23
Hi is there something in linux that tests a hard drives health like for bad sectors etc. I remember some years back i downloaded something for a seagate drive from the manufacturers website called sea tools. I cant remember all the ins and outs of it .

---

### Post by sudodus on 2013-09-23
You can often get a summary in a bios menu. If you want more details, there is ***smartctl***, that you install with smartmontools.
```

sudo apt-get install smartmontools
```

You might also have palimpsest, gnome-disks or some other simplified tool depending of version and flavour of Ubuntu.

---

### Post by rapattack on 2013-09-23
Thanks where do i find it ? I tried to run it via the commandline but it says the command is not found

---

### Post by sudodus on 2013-09-23
You have to install it with the terminal window command that I gave to you in my previous mail. And then run it with

```
sudo smartctl     # and some suitable options
```

Read the manual ```
man smartctl
```

And you can also search for ***Disk Tool*** or something like that in your menu or dash.

---

### Post by rapattack on 2013-11-13
Oh thanks so much. Sorry i never replied but i didnt know this reply existed as i never got an email notification :0( Now i dont know what machine/hard drive i was talking about so will take me time to remember...thanks

---

### Post by andyfied on 2013-11-13
If you run:
> sudo apt-get install gsmartmontools
You get a nice GUI version too :)

---

### Post by rapattack on 2013-11-14
Thanks i dont remember what machine i was working on so no need for further replies. Could have been any friends machine because i know my two desktops are not playing up right now ...hmmmmm its a mystery

---

