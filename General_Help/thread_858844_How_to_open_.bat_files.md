---
title: "How to open .bat files?"
date: 2008-07-14
forum: General Help
---

### Post by Rickyk on 2008-07-14
I need to know how to open .bat files could anyone help me?

Thanks,
Ricky

---

### Post by Squid Tamer on 2008-07-14
Open them, or run them?

You should be able to open them using gedit or cat (from terminal)

I don't think it's possible to run them, as they are for windows, but there may be some program that allows it.

---

### Post by bilijoe on 2008-07-14
With [MS]DOS.

".bat" files are the DOS equivalent of script files.  I'm not an expert on the subject, but I don't believe Linux, or any other OS that uses (shell) script files will recognize DOS .bat files.  The best I can suggest is to read the .bat file to determine what it is intended to do, and then write a script file to do the same.  You'll have to review the documentation for the shell you are using (Ubuntu uses bash, by default, but there are others), in order to find out what commands it responds to, and the proper syntax for each.  In DOS, this was pretty much just a convenient way to avoid typing the same group of commands over and over.  In Linux (and Unix, and ?...) script files can, if you are clever enough, constitute a mini-programming language.  There's a tremendous amount of power available through the Linux command line.

Hope this helps.

---

### Post by Rickyk on 2008-07-14
> **bilijoe said:**
> With [MS]DOS.

".bat" files are the DOS equivalent of script files.  I'm not an expert on the subject, but I don't believe Linux, or any other OS that uses (shell) script files will recognize DOS .bat files.  The best I can suggest is to read the .bat file to determine what it is intended to do, and then write a script file to do the same.  You'll have to review the documentation for the shell you are using (Ubuntu uses bash, by default, but there are others), in order to find out what commands it responds to, and the proper syntax for each.  In DOS, this was pretty much just a convenient way to avoid typing the same group of commands over and over.  In Linux (and Unix, and ?...) script files can, if you are clever enough, constitute a mini-programming language.  There's a tremendous amount of power available through the Linux command line.

Hope this helps.

This went straight over my head and i have no idea on how to script ect. ive only had the os for 2 weeks.

---

### Post by BluePlum on 2008-07-14
He said " Linux won't run bat files, bla bla bla bla, If you want it to run, Open it in txt form and see what the code is intended to do. Write it as a script ( the equivalint of a linux .bat file ) if you wan't it to run in linux "

Hope that helps :)

---

### Post by bilijoe on 2008-07-14
> **Squid Tamer said:**
> You should be able to open them using gedit or cat (from terminal)

I don't think it's possible to run them, as they are for windows, but there may be some program that allows it. Actually, Windows doesn't recognize .bat files directly either; they are a pre-Windows, DOS relic.  To run them from within Windows, you have to open a command window (which essentially means revert to DOS), and run them from the [DOS] command line.  If you just double click on one from the Windows GUI, I think Windows will open a command window for you, and pass the .bat file to it.  .bat files are just text files (as are script files).

Little known fact: until the advent of Windows NT, Windows itself was NOT an operating system--it was nothing more than an [admittedly rather complex] DOS program.  DOS was the operating system, and had to be up and running before Windows could be launched.  It was just a fancy DOS application, nothing more.  NT (which stands for "New Technology") was the first version of Windows that qualifies as an operating system.

---

### Post by Rickyk on 2008-07-14
> **BluePlum said:**
> He said " Linux won't run bat files, bla bla bla bla, If you want it to run, Open it in txt form and see what the code is intended to do. Write it as a script ( the equivalint of a linux .bat file ) if you wan't it to run in linux "

Hope that helps :)



Thank you And do you have any idea how to do this? i i were to post whats in the file could someone re-code it for me?

---

### Post by Canis familiaris on 2008-07-14
Could you post the contents of the BAT file?
I think you need DOSBOX.

---

### Post by Rickyk on 2008-07-14
ok here it is

@echo off

title Initialize

java -Xmx1000m -cp .;Theme.jar Gui 0 0 highmem members 32

pause

---

### Post by Canis familiaris on 2008-07-14
> **Rickyk said:**
> ok here it is

@echo off

title Initialize

java -Xmx1000m -cp .;Theme.jar Gui 0 0 highmem members 32

pause

I guess you are tyring to tun a .jar JAVA file. But what exactly do you intend it ot do?
Since JAVA is cross platform, you may be able to run the Java program in Linux.
Refer to the syntax of the java command though man pages.
```
man java
```

---

### Post by Rickyk on 2008-07-14
> **Anurag_panda said:**
> I guess you are tyring to tun a .jar JAVA file. But what exactly do you intend it ot do?
Since JAVA is cross platform, you may be able to run the Java program in Linux.
Refer to the syntax of the java command though man pages.
```
man java
```


Hmmm? 

Well ill try to give all the info i can, on my bros computer (windows) when you open the .bat file it opens a command line window and runs some stuff then opens a client for a java based game (runescape) but its a private server, if you dont know what runescape is then nvm about the private server

---

### Post by BluePlum on 2008-07-14
Answer to your question you asked me before: No i don't no how to convert your code into a script. 

And you play runescape o.o, thats not lame... :P

---

### Post by Rickyk on 2008-07-14
> **BluePlum said:**
> Answer to your question you asked me before: No i don't no how to convert your code into a script. 

And you play runescape o.o, thats not lame... :P

kk, and i wasnt saying that there was anything wrong with it, just didnt know if you knew what it was and since you know what runescape is i have to run it on the unsigned java thing because when i run it normally it says:

Error_loader_nocache - Unable to create cache directory.

Runescape was unable to find a suitable place to store its temporary files. There are 4 possible solutions:
Log-in as an administrator
Log-in to your computer as an 'administator' user, and then try loading RuneScape again. This should give it sufficient access to create its temporary cache.


Create directory manually
Create a new directory called c:\rscache or /rscache. If possible, set that directory to have full read+write permissions so that all users can write to it. Runescape should then detect that directory and use it for its files.

Try running in the windows Client
Try downloading the RuneScape Windows Client by clicking here, and use that to play the game. The windows client launches RuneScape directly from your desktop. (Requires Internet Explorer 6 or above).


Unsigned Applet
As a last resort you can tell RuneScape not to store any files on the harddisk. This will cause the game to load slower, and also won't fix the 'high detail' version of the game.

    * Go to the RuneScape home page.
    * In the 'Play now' menu, choose 'Java Options'.
    * Select 'Unsigned applet' and finally click 'Save Settings'. 



Then i downloaded the client that launches it from the desktop and i go to load the world and i get a black screen and the home upgrade to members ect so the game "window" isnt loading. I am useing WINE to open the .exe

---

### Post by Sam324 on 2008-08-14
Here ya go,
[http://winehq.org](http://winehq.org)
Not sure if it runs BAT though.

---

### Post by bnorman93 on 2010-03-31
@ECHO OFF

TITLE MHTY Scripts

SET cc=javac
SET cflags=
SET scripts=Scripts
SET scriptspre=%scripts%\Precompiled
SET jarpathfile=Settings\path.txt

IF NOT EXIST "%jarpathfile%" (
	ECHO Path file does not exist. Please run MHTY and try again.
	GOTO end
)

FOR /F "delims=" %%G IN (%jarpathfile%) DO SET jarpath=%%G

CALL FindJDK.bat

IF NOT EXIST %scripts%\*.java (
	ECHO No .java script source files found.
	GOTO end
)

ECHO Compiling scripts
ECHO. > "%scripts%\.class"
DEL /F /Q "%scripts%\*.class" > NUL
"%cc%" %cflags% -cp "%jarpath%" %scripts%\*.java

:end
PAUSE
EXIT




I would really appreciate if someone recoded that to ubuntu for me i just started using ubuntu and dont really know code that well

---

### Post by bnorman93 on 2010-04-01
> **bnorman93 said:**
> @ECHO OFF
 
TITLE MHTY Scripts
 
SET cc=javac
SET cflags=
SET scripts=Scripts
SET scriptspre=%scripts%\Precompiled
SET jarpathfile=Settings\path.txt
 
IF NOT EXIST "%jarpathfile%" (
    ECHO Path file does not exist. Please run MHTY and try again.
    GOTO end
)
 
FOR /F "delims=" %%G IN (%jarpathfile%) DO SET jarpath=%%G
 
CALL FindJDK.bat
 
IF NOT EXIST %scripts%\*.java (
    ECHO No .java script source files found.
    GOTO end
)
 
ECHO Compiling scripts
ECHO. > "%scripts%\.class"
DEL /F /Q "%scripts%\*.class" > NUL
"%cc%" %cflags% -cp "%jarpath%" %scripts%\*.java
 
:end
PAUSE
EXIT
 
 
 
 
I would really appreciate if someone recoded that to ubuntu for me i just started using ubuntu and dont really know code that well
Someone please i need this file to tryout my bot lol

---

### Post by Jeffster999 on 2010-04-01
Where did that bat file come from? And one thing I have not seen posted is the reminder that if you do not know what it will do, then creating/running a script could have detrimental effects on your system.

also check out this site:

 [http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html#toc5](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html#toc5)

---

### Post by Jeffster999 on 2010-04-01
well, i see that part of it was answered in the time it took me to peck out my other post

Damn the gui it has ruined typing

---

### Post by degarb on 2012-04-21
I find the linux command line daunting to say the least.  Dos is simpler, less to learn.  And more powerful because there are hundreds of thousands of dos programs to do anything the command line itself lacks.

I spent months writing a batch ripper for books on cd, which would lookup tag and encode to 21 kps mp3 with no human interaction.  Done with dos.  Then a stream ripper that has features lacking in streamripper.  

also, my own podcatcher that can do all the things I need and lacking in any open source catcher or commercial.

You can automate things in any way you wish with little knowledge, research, programming experience, learning curve, or time.

I spent a month perfecting my weather script that downloads, crops, animates, uploads to ftp.  And alerts to comming rain.  Now, I cannot run the dos script with linux.

Dosbox would not only need to run a single dos ap, but the bat, the aps that the bat calls.  And emulate at least a c: drive.  

Can it do this? 
----

Unlock the door people, and maybe you will slowly gather the userbase to over turn Windows as a primary OS.  Spending 3 years to reinvent the wheel in linux that I did in 6 months in dos/ahk, cannot be an option.   Nor is running a virtualbox that would take a third of my ram on an already slow machine.

---

### Post by oldos2er on 2012-04-22
Closed. Please don't bump old threads.

"If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful."

---

