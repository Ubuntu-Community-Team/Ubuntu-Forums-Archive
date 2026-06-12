---
title: "1005pe brightness issues"
date: 2010-04-06
forum: Hardware
---

### Post by Bennetto on 2010-04-06
Hello all I am having that common random brightness issue problem with 9.10. Now before you post I am going to walk you through what I have done. I was following the original post [here]("http://ubuntuforums.org/showthread.php?t=1412922").

Here is what I did.

[LIST=1]
[*][COLOR=#000000][FONT=Arial]sudo gedit /etc/default/grub      (but this file was empty)[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]Because it was empty I just added this line  [/FONT][/COLOR][COLOR=#000000][FONT=Arial]GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi_osi=Linux"   
[/FONT][/COLOR]
[*][COLOR=#000000][FONT=Arial]I typed    [/FONT][/COLOR][COLOR=#000000][FONT=Arial]sudo update-grub2       command not found so I just ran update-grub[/FONT][/COLOR]
[/LIST]
It still does not work. Thank you for your help.

---

