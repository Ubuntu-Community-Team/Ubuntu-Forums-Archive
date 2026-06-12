---
title: "Cannon PIXMA ip 1600"
date: 2005-10-15
forum: Hardware &amp; Laptops
---

### Post by AlexandertheGreat on 2005-10-15
Is there any member of this forum, that managed to install the specific printer to his system (Ubuntu ver 5.10)  ? 

I have the same printer but my computer doesn't detect it.

---

### Post by Danbla on 2005-10-18
I have the same Printer and the same Problem, i tried Turboprint aswell with the same result. Cant find Linux support on this Printer.
Any help would be welcome :)

mfg
Dan

---

### Post by AlexandertheGreat on 2005-10-22
Perhaps the only way that we can install our printer can be found to this website.

[http://www.lowlevel.cz/log/pivot/entry.php?id=40](http://www.lowlevel.cz/log/pivot/entry.php?id=40)

I have tried to follow this solution path but it doesn't work with the specific model of Cannon. If we had a model like ip3000 and above we might have managed to install it until now.

I hope we find a solution because i don't like the dual boot systems :confused:

see you later (From Greece with love)

---

### Post by InvIsiBlekID on 2005-10-25
im having the same problem with my Canon Pixma iP1600, any help would be appreciated!

---

### Post by Danbla on 2005-10-26
I have checked all Linux Printing Databases know to men.. ;)
Nothing found thou :/ It seems its not only not supported but also not even listed unter not supported.
My guess is, our printer is pretty new, and got no support(yet), since i need i printer now, i am going to return it to the shop and get another one, prolly a hp or epson.

---

### Post by Danbla on 2005-10-28
Today i got a reply from turboprint.de.
They said something like this:
(translated from german)

"We plan a driver at around the end of the year. With this modern printers from Canon, its is hard to get the documentation for those so its not sure yet if the driver is realiseable"

I brought the printer back today and got a HP.
Check [www.linuxprinting.org](www.linuxprinting.org) for Hardware compatibility.

mfg
Dan

---

### Post by AlexandertheGreat on 2005-11-04
[QUOTE=Danbla]"We plan a driver at around the end of the year. With this modern printers from Canon, its is hard to get the documentation for those so its not sure yet if the driver is realiseable"[/QUOTE]

Dan, these are good news. 

&#921; was almost sure that all the ip series printers are suported by linux. Unfortunatelly my info was false about the specific printer.

I cannot change it to the store i got it. So i will just have to wait until the end of the year. I hope i 'm lucky and perhaps i will be able to print ... next year :rolleyes: 

Again thanks for the info Dan . :D

---

### Post by AlexandertheGreat on 2005-11-24
A member (**mr_niceguy**) of this forum managed to install the ip 1500 cannon printer

Here you can find the solution
[http://www.ubuntuforums.org/showthread.php?t=93265](http://www.ubuntuforums.org/showthread.php?t=93265)

I tried to use the same solution for my ip1600 cannon and it didn't work :( :( 

I hope someone solves the installation problem for our printer :???:

---

### Post by chiefofthejojos on 2006-03-11
Turboprint has finished their driver for the ip1600! I'm using it right now and it looks great! Of course, you have to pay the cost of a new cartridge to get rid of the logo on your printouts, but I think I can live with the logo.

EDIT:  On second thought, now I see that the logo print at an apparently random position on the page each time.  That may be a little harder to live with.  At least I get to see what I could have.

---

### Post by Hairback357 on 2006-03-31
I tried the Turboprint myself and it does work great. I had to change the permissions on the printer to get it to print but other than that no problems. I used: sudo chmod 777 /dev/usb/lb0 to enable printing. The only thing that is causing me an issue is the cost of the progrm. 30.00???? that's a little steep since I got the whole printer for 40.00. I haven't decided if I am gonna pay it yet.

---

### Post by Corcorelli on 2006-04-21
I'm also using Turboprint and am also too cheap to pay the thiry euros (which is about what I paid for the printer). I've found that it if you set the print density to 300 then you don't get any logos. This works fine for me as I only want to print documents, not photos. When I'm feeling richer I will buy a full license as it seems to be an excellent application and those guys have to eat;) .

---

### Post by Hairback357 on 2006-04-21
Well I will tell ya what I did. I went to Newegg and ordered a HP 3940. It works perfect in Linux and I paid 40.00 for a whole new printer. I like it better than the Canon anyway because it is smaller and fits in my truck better. Now I have a like new Pixma 1600 just sitting around collecting dust. The cartridges for the HP are a lot cheaper to.

---

### Post by chiefofthejojos on 2006-04-22
[quote=Corcorelli]I'm also using Turboprint and am also too cheap to pay the thiry euros (which is about what I paid for the printer). I've found that it if you set the print density to 300 then you don't get any logos. This works fine for me as I only want to print documents, not photos. When I'm feeling richer I will buy a full license as it seems to be an excellent application and those guys have to eat;) .[/quote]

I tried to set the depth to 300 but I still get the logos.  Are there any other settings you changed?

---

### Post by Hairback357 on 2006-04-22
I also tried setting the settings down to 300dpi and I still got the Logos on my printings. That's when I got fed up and got me a new printer.

---

### Post by chiefofthejojos on 2006-04-27
[quote=chiefofthejojos]I tried to set the depth to 300 but I still get the logos.  Are there any other settings you changed?[/quote]

I printed a map today, and the 300 dpi settings had kicked in.  I guess it takes a reboot or something.  I no longer get the logos on b&w 300 dpi printouts.  Thanks for the workaround, Corcorelli!  Maps are still very readable under 300 dpi.

---

### Post by AlexandertheGreat on 2006-05-24
Does anyone knows where i can find this driver for the printer ; I don't mind about the logo that appears in any page. Please help !!](*,)

---

### Post by chiefofthejojos on 2006-05-24
[http://www.turboprint.de/](http://www.turboprint.de/)

---

### Post by crobard on 2006-08-15
The driver for IP1600 is not yet developped (except the turboprint one but it's not free). You can show your interest in such driver at the following link :

[http://www.canon-europe.com/Support/Software/Linux/registration.asp?ComponentID=312222&SourcePageID=312225#1](http://www.canon-europe.com/Support/Software/Linux/registration.asp?ComponentID=312222&SourcePageID=312225#1)

---

### Post by jdpipe on 2006-08-15
I think that it *should* be possible to install the iP1600 using the free Canon linux drivers. See this page: 
[http://gentoo-wiki.com/Canon_pixma_series](http://gentoo-wiki.com/Canon_pixma_series)

Then adapt the instructions given at
[http://www.ubuntuforums.org/showthread.php?t=204853](http://www.ubuntuforums.org/showthread.php?t=204853)

(substitute references to 'ip4200' with 'ip2200').

I haven't tried this although I recently went through the process with the Canon Pixma MP760 printer and the Canon drivers worked ok for me.

Cheers
JP

---

### Post by tristan@Ubuntu on 2006-08-20
> **jdpipe said:**
> I think that it *should* be possible to install the iP1600 using the free Canon linux drivers. See this page: 
[http://gentoo-wiki.com/Canon_pixma_series](http://gentoo-wiki.com/Canon_pixma_series)

Then adapt the instructions given at
[http://www.ubuntuforums.org/showthread.php?t=204853](http://www.ubuntuforums.org/showthread.php?t=204853)

(substitute references to 'ip4200' with 'ip2200')

JP

thanks for that, but I need more details. What are you doing with the gentoo script? I see no connection between your first link and the second one... I would greatly appreciate some more detail.
Tristan

---

### Post by michaeljt on 2006-09-08
This is probably a silly question, but I suppose that you have tried out all the Canon drivers in Gutenprint 5 (including BJC ones and others) to see if one of them works or partially works for you printer?

---

### Post by flyakite on 2006-11-30
> **jdpipe said:**
> I think that it *should* be possible to install the iP1600 using the free Canon linux drivers. See this page: 
[http://gentoo-wiki.com/Canon_pixma_series](http://gentoo-wiki.com/Canon_pixma_series)

Then adapt the instructions given at
[http://www.ubuntuforums.org/showthread.php?t=204853](http://www.ubuntuforums.org/showthread.php?t=204853)

(substitute references to 'ip4200' with 'ip2200').

I haven't tried this although I recently went through the process with the Canon Pixma MP760 printer and the Canon drivers worked ok for me.

Cheers
JP

Thanks a lot,
it works like a charm!!

---

### Post by blunile on 2006-12-22
> **jdpipe said:**
> I think that it *should* be possible to install the iP1600 using the free Canon linux drivers. See this page: 
[http://gentoo-wiki.com/Canon_pixma_series](http://gentoo-wiki.com/Canon_pixma_series)

Then adapt the instructions given at
[http://www.ubuntuforums.org/showthread.php?t=204853](http://www.ubuntuforums.org/showthread.php?t=204853)

(substitute references to 'ip4200' with 'ip2200').

I haven't tried this although I recently went through the process with the Canon Pixma MP760 printer and the Canon drivers worked ok for me.

Cheers
JP

Well I tried this method but it didn't work. My ubuntu detects 2 ip 1600 printers (although i have only one ) . I installed the ip2200 driver but it didn't work out . Anybody have ideas how can i fix this ??

I didnt like turbo print so please don't suggest it.

Thank you in advance :-k

---

### Post by blunile on 2006-12-22
NO I managed the problem .IT turned out that one of the the two detected printers only work.

Thank u and God bless you All  :-D

---

### Post by sberka on 2007-03-05
I installed the driver for ip1600 and it prints very nicely.  Used ip2200 drivers from Canon with a lot of help from the forums.  Thanks a lot to all of you, especially elinux from freespire forum!  All summarized [[COLOR="Blue"]here[/COLOR]]("http://www.berka.name/phpwiki/index.php/Kubuntu%206.0.6%20%28Dapper%29").

---

### Post by kaj on 2007-05-05
Somebody might be interrested to know, that when the iP2200 drivers are installed, a *.ppd file is placed in: /usr/share/cups/model

In Ubuntu 7.04 Feisty the driver for iP2200 wasn't autodetected, but I clicked on 'Install a driver'
Only .ppd files are accepted, and i found canonip2200.ppd, and it works.

Kaj

---

### Post by ramjet_1953 on 2007-05-05
Kaj got it going, with a bit of tweaking.

Follow this link:

[http://ubuntuforums.org/showthread.php?t=433187](http://ubuntuforums.org/showthread.php?t=433187)

Regards,
Roger :cool:

---

