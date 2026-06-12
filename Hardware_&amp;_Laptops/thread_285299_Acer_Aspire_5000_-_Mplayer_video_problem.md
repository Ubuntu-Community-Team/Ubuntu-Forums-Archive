---
title: "Acer Aspire 5000 - Mplayer video problem"
date: 2006-10-26
forum: Hardware &amp; Laptops
---

### Post by elias85 on 2006-10-26
I get this error "Error opening/initializing the selected video_out(vo) device" when i 'm trying with mplayer to run an avi file. If I try to play that avi file from command line, it plays perfectly.When i had open suse 10.1 before it was working...Any suggestions?[uing acer aspire 5000 with onboard vga]

---

### Post by autosuggested on 2006-11-10
> **elias85 said:**
> I get this error "Error opening/initializing the selected video_out(vo) device" when i 'm trying with mplayer to run an avi file. If I try to play that avi file from command line, it plays perfectly.When i had open suse 10.1 before it was working...Any suggestions?[uing acer aspire 5000 with onboard vga]

Hi Elias, 

Like you, I was getting a "Error opening/initializing the selected video_out (-vo) device." error message. I'm guessing you're using the mplayer GUI to open your video files? If so, open up a terminal and type in the following:

```
gedit ~/.mplayer/gui.conf
```

Near the start of the file you should see an entry for vo_driver? Change it to read

```
vo_driver = "xv"
```

Save the file and hopefully you won't have a problem the next time you open up a .avi or similar.

// autosuggested

---

