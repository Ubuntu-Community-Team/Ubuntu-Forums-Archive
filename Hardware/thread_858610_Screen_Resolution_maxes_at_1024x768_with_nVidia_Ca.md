---
title: "Screen Resolution maxes at 1024x768 with nVidia Card"
date: 2008-07-13
forum: Hardware
---

### Post by JacobW on 2008-07-13
Greetings, 
     I have just installed, (two days ago) Hardy on my Desktop.  Everything is working great except for the fact that I have an nVidia 6200(?) AGP graphics card installed and the max resolution I should have is 1280 x 1024.  However, my current max resolution is 1024 x 768.  I have searched through the forums and followed [this]("http://ubuntuforums.org/showthread.php?t=854065&highlight=nvidia+GeForce") link. I have also followed the detailed directions offered [here]("http://ubuntuforums.org/showpost.php?p=5086971&postcount=6"). However, I still cannot view a resolution of 1280 x 1024.  I'm sure there have been solutions found for this type of problem and I do apologize, but I haven't been able to find it.  Any help would be greatly appreciated! 

Thanks!
Jacob

---

### Post by JacobW on 2008-07-14
--Update--
I have been researching this problem more and I found, on some random website, the command: ~$nvidia-settings which I can use to bring up a settings window and change the max resolution here. The problem now is that once I change it here, I click on the button that tells it to write to the xorg.conf file and I get an error that tells me that it can't backup the xorg.conf file. Therefore, when I reboot, it reverts back to the old 1020 x 768 resolution as before. Does anyone know why this might be happening?

---

### Post by JacobW on 2008-07-15
---Another Update---
Well, I kept looking and although I couldn't find anything on why my resolution kept resetting I couldn't quite shake the feeling that it had something to do with the xorg.conf file. So, upon a restart, I entered: $nvidia-settings into the command line and changed the settings on the nvidia screen. Then, because the newly updated xorg.conf file wouldn't get saved because the system couldn't back up the old one, I manually backed it up. Command line: $cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup 
Meanwhile, while I was still in the nvidia settings window I clicked on the button to save to the xserver, (or whatever the button said, sorry I can't remember exactly). A dialog box opened asking which X - file to save the new settings to. I clicked on the 'Preview' button on the dialog box and copied the text in the new xorg file.  Then, back at the command line, I entered: gkduso gedit /etc/X11/xorg.conf and pasted the newly copied text into the file. I then saved it and closed out of everything and restarted. When the system was back online I realized to my utter joy that the resolution settings were kept and I was in business. Hopefully, this will help others new ubuntu users like myself from 3 days of experimentation and a re-install of everything.  Enjoy!

---

### Post by Ray Hunt on 2008-09-09
you could also have done this from CLI

$ sudo nvidia-settings

entered your login pass then used the settings GUI as a superuser to save settings.

---

