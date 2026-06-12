---
title: "Brother DCP 7030"
date: 2012-11-20
forum: Hardware
---

### Post by offgridguy on 2012-11-20
Hello;  Once again i want to try to get my Brother DCP 7030 to print, with ubuntu.
I had it working once via the install script until i had to do a OS reinstall.  I will post some
of the links i have been using.  Thank you for looking

[http://ubuntuforums.org/showthread.php?t=2066923](http://ubuntuforums.org/showthread.php?t=2066923)
[http://ubuntuforums.org/showthread.php?t=2022353](http://ubuntuforums.org/showthread.php?t=2022353)
[http://www.brother.com/cgi-bin/agree...ng=English_lpr](http://www.brother.com/cgi-bin/agree...ng=English_lpr)
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104)
[http://myubuntux.wordpress.com/2011/...-ubuntu-linux/](http://myubuntux.wordpress.com/2011/...-ubuntu-linux/)
[http://ubuntuforums.org/showthread.php?t=590793](http://ubuntuforums.org/showthread.php?t=590793)
This last site appears to use tools not available on my unity DE.

I am not sure what i'm missing, all help appreciated.
edit; thank you for moving this thread, and changing the title                                                                                     :)

---

### Post by pdc on 2012-11-21
have a read at post #5 in this thread

[http://ubuntuforums.org/showthread.php?p=12342527#post12342527](http://ubuntuforums.org/showthread.php?p=12342527#post12342527)

........in it I suggested to mamba801 that he COPY the text of the brother [COLOR="Magenta"]installer script[/COLOR]; and then run it in his system; he did that, and it worked well; 

.... he gives excellent, most detailed, steps of what he did ...

......

EDIT: I now see you feature in post #7 of this thread...................  follow the steps mamba801 details............

---

### Post by offgridguy on 2012-11-22
Thank you for your reply.  I will have another try at this,
The problem i seem to be having, is finding the script with the terminal, i keep getting the no such file or directory error.  It doesn't help that i am very much a
neophyte at using the CLI.
    I did copy the script from the brother site, saved it on gedit in downloads, so i
have it in text form.
   The steps mambo 801 mentioned about permission, is a step i had been
missing. I used to get permission denied error message.  
    Anyway i will try later this evening as i have to step away for a while.

Thanks again for your interest.

---

### Post by pdc on 2012-11-22
> The problem i seem to be having, is finding the script with the terminal, i keep getting the no such file or directory error

> I did copy the script from the brother site, saved it on gedit in downloads

............great..............you likely saved it to the Downloads directory

.....can I suggest  ...if you copied and pasted the Brother script into gedit .........and saved it as ........[COLOR="Magenta"]offgridguy.sh[/COLOR]

...**use the GUI** ... meaning mouse-click it all ............

so click and open your Downloads folder; [COLOR="Blue"]right-click[/COLOR] on the file you called [COLOR="Magenta"]offgridguy.sh[/COLOR]

....click on the middle tab..........[COLOR="SeaGreen"]permissions[/COLOR]........

(as in the thumbnail enclosed below...........)

......select [COLOR="SeaGreen"]EXECUTE[/COLOR] and having clicked, close that window..

then go back and [COLOR="Blue"]left click[/COLOR] on [COLOR="Magenta"]offgridguy.sh[/COLOR] (*or whatever you have called it* ..)

and you get the view run.png as shown below

.....select [COLOR="Blue"]run in terminal[/COLOR] as then you can enter your printer model etc ..

....I think you will be pleasantly surprised how well it all goes, and you can look forward to using your very good printer ...........

---

### Post by offgridguy on 2012-11-22
Hello pdc;  I am now the newest member of your fan club.  Thank you so much.
    My linux computer is once again a useful office tool and not just an email checker.
:):):):)

---

### Post by pdc on 2012-11-23
delighted to hear it all worked! Enjoy! :)

---

### Post by shakiaforum on 2012-11-23
My linux computer is once again a useful office tool and not just an email checker

---

### Post by shakiaforum on 2012-11-23
The computer is not easy to handle.

---

### Post by offgridguy on 2013-02-22
An update here;  again i have used this method to install printer drivers successfully .
This  time using  Linux Mint 14,  works well, but helps that i have previous experience.

For anyone doing this the first time, there is one difference to note from post #4,
were it says this
> then go back and [COLOR=Blue]left click[/COLOR] on [COLOR=Magenta]offgridguy.sh[/COLOR] (*or whatever you have called it* ..)  
Here I had to double left click to bring up the desired menu.  Again whenever i use this
i am grateful to pdc.   :D:D

---

### Post by pdc on 2013-02-22
many thanks offgridguy; well done; you are becoming a bit of an expert at all of this! Enjoy Mint; it is becoming our main distro here

---

