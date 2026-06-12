---
title: "[SOLVED] scripting applications...."
date: 2008-08-04
forum: General Help
---

### Post by mfaust731 on 2008-08-04
Hello all,

Im a somewhat seasoned linux guy, and have only recent discovered the power of shell scripts.

my question is how can I script applications?

Most shell scripts ( that I have seen anyway ) work with files or folders that exist on the computer. I would like to for instance, start firefox, got a webpage, print it to pdf, and email it to me everyday @ 6 am.

How can a script interact that way in Linux?
In the windows world I have extensivly used Autoit to do similar actions - just never figured it out with Ubuntu

Thanks

---

### Post by ghostdog74 on 2008-08-04
> **mfaust731 said:**
> Hello all,

Im a somewhat seasoned linux guy, and have only recent discovered the power of shell scripts.



my question is how can I script applications?

Most shell scripts ( that I have seen anyway ) work with files or folders that exist on the computer. I would like to for instance, start firefox, got a webpage, print it to pdf, and email it to me everyday @ 6 am.

How can a script interact that way in Linux?
In the windows world I have extensivly used Autoit to do similar actions - just never figured it out with Ubuntu

Thanks

you might want to take a look at the bash manual link in my sig to learn some bash scripting.

---

### Post by mfaust731 on 2008-08-04
ill check it out

Thanks

---

### Post by mfaust731 on 2008-08-05
ok, I have read through the manuals and I still see no way a script to interact with a gui program as in my example.

If I could do this with bash, could someone please post a snippit to show me how

Thanks

---

### Post by rfdeshon on 2008-08-05
> **mfaust731 said:**
> ok, I have read through the manuals and I still see no way a script to interact with a gui program as in my example.

If I could do this with bash, could someone please post a snippit to show me how

Thanks

It all depends on the program. All bash scripting really does is executes programs... so... you would need to check out the command line options for the program you are running to see if it can do what you want it to. I know that you can launch firefox with a url like this:
```
firefox -url http://www.firefoxfacts.com
``` I have no idea if it's possible to print the page from the command line though.

---

### Post by TreeFinger on 2008-08-05
You aren't going to interact with a GUI program.

I'd say the psuedo code for this would be.

1) Download Webpage to local harddrive
2) Convert HTML file to PDF (Not sure if there is an application for this.)
3) send file to e-mail

---

### Post by mfaust731 on 2008-08-05
ok, that more the lines I was thinking for a shell script, Is there NO program to d o this in linux?

Basically, I want to record my actions as I manaully do it, this have the ability to repeat those saved actions via cron

---

### Post by ibuclaw on 2008-08-05
Look up Zenity.

It is fairly verbose, but once you work out how it works you can get some nifty gui based scripts :)

```
zenity --info --text="Hello World"
```

```
man zenity
```
for more info.

or have a read through at this app here to get to grips with it:
[http://ppa.launchpad.net/kiwilinux-members/ubuntu/pool/main/r/restoregrub/](http://ppa.launchpad.net/kiwilinux-members/ubuntu/pool/main/r/restoregrub/)

Regards
Iain

---

### Post by meatpan on 2008-08-05
> **mfaust731 said:**
> Hello all,
I would like to for instance, start firefox, got a webpage, print it to pdf, and email it to me everyday @ 6 am.


Good general comments on usage of shell scripts in this thread.  If you need help with the idea above, consider creating a script with the following utilities:

wget:  Provides programatic access to web content.  Simple run 'wget <url>'.  Some powerful options are available for refining your fetch query.
crontab: Schedule a task to execute at a regular interval.
mail:  send an email message

You can form quite a few interesting combinations with these programs:
o  Write a script that runs wget to fetch some info (such as a pdf).
o  Move the pdf to a folder
o  email yourself via 'mail', with the pdf, or location of the folder
o  Write a little usage statement and some error handling.  Take a look in /etc/init.d for some great example scripts.

Next, schedule this script to be routinely executed using crontab (check out the manual on cron.  These are powerful commands).

---

### Post by mfaust731 on 2008-08-05
I thought zenity was used to make pop ups, from shell scripts

---

### Post by rfdeshon on 2008-08-05
> **mfaust731 said:**
> ok, that more the lines I was thinking for a shell script, Is there NO program to d o this in linux?

Basically, I want to record my actions as I manaully do it, this have the ability to repeat those saved actions via cron

Thats not a script, that's a macro. A macro is a recorded set of inputs and would require a separate program to create and run the macro as far as I know. Also, most anything that can be done with a macro can be done with some creative shell scripting. For your above program, it sounds like you should write a shell script that uses wget to grab the webpage in question, then find an HTML to pdf converter (I know there are some, but not in the repository that I have seen) or, what I would recommend HTML to postscript (html2ps is in the repos) run that on the html file that you got from wget then use mail or some other command line program to email the postscript file to you.

---

### Post by mfaust731 on 2008-08-05
If anyone finds this thread with a similar task " xnee" is the program you want.

thanks

---

### Post by colobix on 2008-08-05
You want to start programs and tasks by time and date right? There are many programs for thins like this in Ubuntu.
Try this. Click System, administration, services. Now lock up the program pack there.

---

