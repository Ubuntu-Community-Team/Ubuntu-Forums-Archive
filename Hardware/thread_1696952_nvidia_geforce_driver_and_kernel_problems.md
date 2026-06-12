---
title: "nvidia geforce driver and kernel problems"
date: 2011-02-28
forum: Hardware
---

### Post by Fodderuntu on 2011-02-28
I have been trying for 3 days.... 3 days!!! to get my 9800GT to stop running the fan at 100% and you did it UrbenLegend! no other post mentioned the AGE of the GCC required - i followed your tip and BAM! silence! i registered just to say thank you! so for others reading this my GCC with Ubantu 10.10 was too new for the nvidia drivers to compile!! so I used these steps....


 

 
[LIST]
[*]download this relevant file -     [http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)
[*]while its downloading goto system     > admin > synaptics package manager &#8211; scroll down the list     and tick the box for GCC 4.1 and apply it
[*]when the download completes, open     terminal, type "sudo" then drag the downloaded file into     the terminal window - you should get some text like
[LIST]
[*]"sudo         '/home/john/Desktop/NVIDIA-Linux-x86_64-173.14.28-pkg2.run'"
[/LIST]
 
[*]it wont work but we are just     saving the command into termianl for later use
[*]NOTE &#8211; the process will NOT work     if the x server (desktop) is running in any form, so you must do     this from console
[*]when you boot to console, login     with your user name and password
[*]then use the up arrow on your     keyboard to scrole through commands until you see
[LIST]
[*]&#8220;sudo         '/home/john/Desktop/NVIDIA-Linux-x86_64-173.14.28-pkg2.run'"
[/LIST]
 
[*]hit enter &#8211; run through the     nvidia prompts
[*]once complete and back to console,     type &#8220;startx&#8221;
[*]your done!
[/LIST]
 

 Thats it, enjoy the silance and the ability to enable cool desktop animations!
 

 Thanks again UrbenLegend

---

