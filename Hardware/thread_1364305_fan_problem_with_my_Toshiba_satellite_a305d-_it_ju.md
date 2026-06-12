---
title: "fan problem with my Toshiba satellite a305d- it just keep going"
date: 2009-12-25
forum: Hardware
---

### Post by spaik on 2009-12-25
[CENTER]> hi

so as the title says i have a problem since i upgraded to ubuntu 9.10. the laptop's fan act normal for like 30 min or so and then keep going as fast as it can for the rest of the time the laptop is on even if im not even running anything or doing anything. its loud and it sure uses battery and life from the fan.

i searched a little bet but haven't found something that could help me. please help me if you know what to do. i upgraded my bios and installed toshiba fxfn and sensors..

thank u all and merry Christmas and happy new year ;)[/CENTER]

ok so i got it to work fine and here is how for anyone having the same problem..... as i said i installed toshiba fxfn and sensors and also upgraded my bios before starting to doing this.. i dont think that anything helped, but maybe the bios update.

steve161 gived me this link to his post that got the how to
> I posted a solution that worked for me on my Toshiba Satellite L305. If you read through the thread, you will see it worked for some, but not others.

[http://ubuntuforums.org/showthread.p...25#post8318825](http://ubuntuforums.org/showthread.p...25#post8318825)

but i had problem as i couldn't find the grub file... so i went to the synaptic package manager and searched for "Grub" and got the "Grub 2" installed from there and that solved the first part, finding the grub file.

so i did what Steve said and it worked for me and here is how to to do if u dont know how.
[CENTER]
open the terminal and type :
sudo nano /etc/default/grub


that should get the grub file opened in the terminal and sudo gives u the power to modify it.

so u add the line like steve said and simply press ctrl+X to exit and save. then type in the terminal :
sudo update-grub

and restart :D 

hope that helps u out there. have a happy new year.[/CENTER]



// Last update //

the problem kicked in again with no reason. the fan starts full power when it reaches 80 and then keep going. :(

---

### Post by IcarusR on 2009-12-26
If your Tosh has a toshiba bios you can use toshiba tools, which I believe should control the fan amongst other things.

[http://www.buzzard.me.uk/toshiba/index.html]("http://www.buzzard.me.uk/toshiba/index.html")

---

### Post by spaik on 2009-12-27
thanks so much, but it didn't work.. something with the instillation coz every time i try to install it it gives me error.

i noticed that sometimes it works normally :D and most the time its loud and fast...

please help if u know a way :)

---

### Post by steve161 on 2009-12-27
I posted a solution that worked for me on my Toshiba  Satellite L305.  If you read through the thread, you will see it worked for some, but not others.  

[http://ubuntuforums.org/showthread.php?p=8318825#post8318825](http://ubuntuforums.org/showthread.php?p=8318825#post8318825)

---

### Post by spaik on 2009-12-28
thanks my friend. it did work for me.....

thanks again everyone.... u r an amazing community :guitar:

---

### Post by spaik on 2009-12-29
still trying to find a way...

---

### Post by spaik on 2010-01-05
did anyone find anything yet?

---

