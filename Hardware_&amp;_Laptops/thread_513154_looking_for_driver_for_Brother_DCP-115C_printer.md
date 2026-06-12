---
title: "looking for driver for Brother DCP-115C printer"
date: 2007-07-30
forum: Hardware &amp; Laptops
---

### Post by danezeq on 2007-07-30
is it possible to use that printer under ubuntu?


thank you all :)

---

### Post by MrHippocampus on 2007-07-30
There is a page filled with linux drivers on Brother's service and support site [here]("http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html"). It says you should use the MFC-210C driver for your DCP-115C, make sure you download the debain package and not the Red Hat version.

I may be wrong but I don't think the drivers are bundled with ubuntu.

Good luck :)

---

### Post by danezeq on 2007-07-30
Are you sure this driver can work on ubuntu?
what does it mean "bundled"?
sorry this is my first day on linux ever!

i've un-packaged the file and it seems go ok.
then i clicked on "terminal" and i saw there is an error message.
is that the reason i cant print? :(
[IMG]http://www.telavivinf.com/linux.jpg[/IMG]

---

### Post by MrHippocampus on 2007-07-31
looks like youll have to install the package "csh" before those drivers will install.

---

### Post by danezeq on 2007-07-31
Thank you for your replies :-)

What does CSH mean? is it a driver? Where can i find it?
thanks again.:)

---

### Post by MrHippocampus on 2007-07-31
```
sudo apt-get install csh
```

Typing that into a terminal should do it. You can also install it in the synaptic package manager.

---

### Post by danezeq on 2007-07-31
Ok, now there is another error message.
the printer has been installed, but it still wont print!

:confused:[IMG]http://telavivinf.com/2.jpg[/IMG]

---

### Post by danezeq on 2007-07-31
Just one another thing:
When i go to printer properties i get this error message. (in the red circle)
is it have something with my problem?

thank you again, it's very nice of you :)

---

### Post by danezeq on 2007-07-31
Just one another thing:
When i go to printer properties i get this error message. (in the red circle)
is it have something with my problem?

thank you again, it's very nice of you :)

[IMG]http://www.telavivinf.com/3.jpg[/IMG]

---

### Post by MrHippocampus on 2007-07-31
Sorry I don't know what to do to solve that, does anybody else know?

---

### Post by danezeq on 2007-08-01
Hello? Anybody?:(

---

### Post by xc3RnbFO8P on 2007-08-01
What happends if you choose A4?

---

### Post by danezeq on 2007-08-01
No
it's still wont printing.
the status of the printer is "STOPPED: job stopped"

---

### Post by cblanquer on 2007-08-03
Exactly the same issue on a friend&#347; computer I am currently trying to fix. USB connection, by the way.
If I find the solution I shall post it. :(

---

### Post by cblanquer on 2007-08-03
Following those instructions I hav got the SCANNER functions work but not yet the printer functions:
[http://ubuntuforums.org/showthread.php?t=486675](http://ubuntuforums.org/showthread.php?t=486675)

Remark:
when setting the usb directory permissions (chmod 666) and logout-login I have found out it did not work because the usb device was assigned to a different code (!!???), I repeated then the chmod 6666 and it worked again.
I have not tested again a logout-login, I hope the device number is not changing again.

---

### Post by cblanquer on 2007-08-03
All the info is here, I deinstalled the CUPS stuff and redid the steps for DCP-115C with MCF-210C:
[http://ubuntuforums.org/showthread.php?t=486675](http://ubuntuforums.org/showthread.php?t=486675)
(no time to post anymore, no access to this friends computer anymore so I hop eI get everything working in max 1 hour & good luck)

---

### Post by cblanquer on 2007-08-03
This is the right link I should have posted: 
[http://ubuntuforums.org/showthread.php?t=105703&highlight=DCP-115](http://ubuntuforums.org/showthread.php?t=105703&highlight=DCP-115)

Soory, I am too tired now...

---

### Post by danezeq on 2007-08-06
Thank you! for the first time i sucseed installing the SCANNER in ubuntu.
but the PRINTER still not working!

i did all the steps written in the post you send me. but i get this error message: "Unable to copy PPD file!"

i saw that there is a special set of command for this case, i wrote them and nothing happend!

this is just frustrating. maybe i need to uninstall that CUPS thing like you?
how did you do that? (plz remember - i'm totally new to linux but determind to lern :-))[IMG]http://telavivinf.com/PPDFILE.jpg[/IMG]

---

### Post by cblanquer on 2007-08-07
Sorry I have no access to the computer I was setting with a Brother DCP-115C anymore for at least 2 years so I can give little help.
I guess the best thing is to re-read and print the right set of instructions and reinstall, either only the printer or either the full stuff.
Actually I cannot see why it does not copy your ,PPD file.
Could it be a problem with permissions in the directory you are working with ? This sounds strange to me as it is standard directory so no special setting should be required there.

I would recommend to do the things again. Maybe there was a mistake.
Think about de-installing before, restarting your PC before doing anything.
(Also your userID should be administrator enabled).
Good luck.

---

### Post by danezeq on 2007-08-07
thank you again:-)

i did it few times, i restarted ofcourse many times as well.
i dont know how to de-install and what exactly do i need to de-install? (what is the FULL STUFF) is it done with a specific command?
i think my userID is administrator enabled.

---

### Post by niceguy123 on 2007-09-05
Dan (or anyone else here),

have you got the DCP 115C running? I have one too and would like to get it running?

---

### Post by danezeq on 2007-11-11
> **niceguy123 said:**
> Dan (or anyone else here),

have you got the DCP 115C running? I have one too and would like to get it running?]

No!!! it drives me crazy!! i still didn't!! :(

---

### Post by PigironBob on 2007-11-16
I have a DCP 115c as well if there is no fix I dunno what I will do. I will not be able to change fully over to Linux like I want to.
What a pain.

---

### Post by wankel on 2008-01-09
Here's a guy claiming success with his DCP-115:
[http://ubuntuforums.org/report.php?p=3671326](http://ubuntuforums.org/report.php?p=3671326)

---

