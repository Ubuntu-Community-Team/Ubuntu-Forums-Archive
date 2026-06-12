---
title: "[SOLVED] Shutdown Ubuntu when program closes"
date: 2008-09-25
forum: General Help
---

### Post by Bradleelee on 2008-09-25
I am running Hardy Heron 8.04 and am attempting to get Ubuntu to completely shutdown when a specific program closes.  I did not know if there is an easy way to get this accomplished. 

If there is not an easy way, then I will take what I can get. Thanks in advance!

---

### Post by Pelham123 on 2008-09-25
Sounds like youre gonna have to make up a script that monitors your 'program' then shutsdown on program exit status or add a shutdown script to the 'program' in question. Bit hard to help without more info really...

---

### Post by wilbbe01 on 2008-09-25
Rather than monitoring the programs process, would it be easier to simply have a script with a line to run the program followed by a line to shutdown?  So long as you don't send the program you are starting to the background it seems as though it would never get to the shutdown line unless the program quit.

---

### Post by jarondl on 2008-09-25
from terminal, use:
sudo -s
someprogram && shutdown now

the && means wait for first task to finish, and run the second one.
 
you need to enter root mode (the -s flag) because running:
someprogram && sudo shutdown now

Sudo is gonna ask for a password.

Good Luck

---

### Post by Bradleelee on 2008-09-25
Thank you very much for the reply. I agree that I was not terribly explicit so I guess I will be now.

I wanted to be able to shutdown Ubuntu when VM Player closes.  Since I have VM Player set to close when the VM shuts down, I was going to try and have Ubuntu shutdown right after.

I hope this clarifies a little bit.  I will give your suggestions a try and I thank you very much for your help!  If what I have said above changes anything then please let me know.

Also, I am running Devil's Pie if that would make a difference.

---

### Post by Bradleelee on 2008-09-25
So I found on this thread how to execute a script on startup:
[http://ubuntuforums.org/showthread.php?t=208954](http://ubuntuforums.org/showthread.php?t=208954)

So I followed the steps as shown:
To run your script on startup do as follow :
1- create a file under init.d : sudo gedit /etc/init.d/my_script
2- put your command lines/script in the file & save it
3- make the file executable : sudo chmod +x /etc/init.d/my_script
4- make it run on boot : sudo update-rc.d my_script defaults

I used the script that you provided and it decided to crash on me. I had to delete the script in order to get it to boot. So there might be a problem.

---

### Post by Bradleelee on 2008-09-30
Anyone have an idea on how to make this into a script?  I am a little lost when it comes to this stuff.

---

### Post by Causer1984 on 2008-09-30
What was in the script?

---

### Post by alberto ferreira on 2008-09-30
Hi, hope I understood it right: you want to shutdown the pc after the VM Player closes?

If that's the case then:

Prerequisites:
 * You have to run the VM Player from the script (to make sure it is a child process of the script)

Script -- The lines after the "#" excluding the first one (#! /bin/bash) are just comments and can be removed, just like the blank lines:
CODE goes here:"
#! /bin/bash
#I don't know the name of the executable of VM Player so you have to find that for yourself (it normally has the name of the program though)

#The following line logs you in as root for the shutdown part
sudo -s

#!!!!!!!!#to run the vm itself delete this entire line and write the name of vm's executable followed by a space and a "&" character

name_of_program #replace "name_of_program" with the name of vm player's executable
#This line is only run when vm player closes and is the one that shuts down your pc
sudo shutdown -h 0
"
Copy the script, save it then right-click it, go to properties>permissions tab>check  "Allow to execute the file as an application"

To make the script run at startup 
Notes: if you want you can set this script to run at startup by going to the gnome-panel>system>preferences>sessions>add>write a name for the task and the command should be the complete path to the script.


This only works if you have the vm running so to run the vm either:
 *do what says in the line that starts by #!!!!!!!!#
 *do as you've done to add the script to startup but this time with the vm and in the command part write the name of the vm's executable
 *launch the vm manually then the script



Hope it's useful :)

---

### Post by Bradleelee on 2008-09-30
@Causer: I was using the script provided by Jarondl which was:

sudo -s
someprogram && shutdown now

However, I am going to try out Alberto's solution next unless you see something wrong with it. Please feel free to add anything though! Any help I can get is more than appreciated.

@Alberto: Thank you very much for the scripting help. I am initially starting VM Player and the Virtual Machine itself through sessions.  Would this change anything as to how your script would operate?  I was planning on calling the script through sessions as well as you had stated in your explanations.

Again I am sorry about all of the questions.  I have never done scripting in this manner before so I greatly appreciate the help.

---

### Post by Causer1984 on 2008-10-01
People may correct me on this, but doesn't vmplayer need X to work?

My betting is that what's happening is that vmplayer is loading before its dependencies are in place (most notably X.) You can play about with the run-levels, but I don't think that Ubuntu even uses init.d any more.

Could you try instead to put that one-liner into ~/.login so that it loads when you log in rather than start the computer? If that works, I think the script would need to be a little meatier so that you don't get multiple instances of vmplayer, but try it first to see if it works OK.

---

### Post by Bradleelee on 2008-10-01
Thank you all.  I am going to try a few of the ideas that are here in the near future.

---

### Post by alberto ferreira on 2008-10-01
Hi again, you don't need to apologize for anything, that's why we're here ;)

Anyways:
If you are already starting VM through sessions you just need to launch vm player with the script from there too and make sure you only type in the password when vm is already launched, so, now that we know entirely what you want here goes the final script (no special comments because it works like the previous one):

```
/#! /bin/bash
sudo -s
name_of_program
sudo shutdown -h 0
```

Notes:
*don't forget to replace "name_of_program" with the name of vm player's executable
*use sessions to launch VM and the script

Request:when your topic has been solved please go to the top of the page and click thread tools>mark thread as solved



If it doesn't work or you don't understand something or you have a doubt don't be afraid to ask.
Good luck

---

### Post by Bradleelee on 2008-10-02
Alright so I tried out the solution provided by Alberto.  I am going to list everything as explicitly as possible as to what I have done so far and what is happening.

Creating the script:
1. gedit vmplayershutdown
2. enter the following text, exactly as is, into the file:
```
/#! /bin/bash
sudo -s
vmplayer
sudo shutdown -h 0
```
3. Press the save button [was saved in /home/user/]
4. Close the window
5. Find the file and change to be able to execute as an application.

Sessions:
I have three added sessions.  One that opens VMPlayer as well as the Virtual Machine itself. Another that calls the script that is written above. And another that starts and executes some commands for Devil's Pie.  The text for each as well as explanations are as follows:
1. The first session opens VMPlayer as well as the Virtual Machine.  The text used in the command line is [Note: I do use the quotations around the path to the virtual machine]:
```
vmplayer "path/to/VM"
```
2. The second is for the script that was written above.  The text used is as follows:
```
"/home/user/vmplayershutdown"
```
3. The third is for devil's pie.  It calls the program and then executes two commands.  It maximizes the window and removes the top window bar from it as well. I dont remember the code that calls the Devil's Pie program off the top of my head, but it has been working before.  However, the code within the text file that devil's pie uses is below:
```
(if
(is (application_name) "vmplayer")
(begin
(maximize)
(undecorate)
)
)

```

---------------------
Now that that is all out of the way, I can tell you what is not working.  Before using the script I have VMPlayer set to automatically close when the Virtual Machine is powered off.  This has been working.  Devil's Pie also maximizes and undecorates perfectly when VMPlayer starts up via sessions.  So no problem there.  The problem occurs when I use the script.  First, when I turn off the virtual machine VMPlayer no longer closes automatically.  Second, when I manually close it Ubuntu does not shut down like it is supposed to according to the script. I have Ubuntu set to automatically log into the OS btw.  I also get no prompt at any time to enter in a password as far as I can see.

I am doing my best this time around to give as much information as possible.  Thanks so much for the help!

---

### Post by alberto ferreira on 2008-10-02
Well, I'm sorry but I made a mistake writing the script - the first line 
should be:
#! /bin/bash , not /#! /bin/bash


If
```

vmplayer "path/to/VM"

```lauches vmplayer and the vm you should not lauch it from sessions but 
rather include it in the script that would then become:

```
#! /bin/bash
sudo -s
vmplayer "path/to/VM"
sudo shutdown -h 0
```So, you would only launch from sessions the script and devil's pie.



The inconvinient is that during the whole session you will have the 
console open, the advantage is that you can close the console manually 
closing vm, vmplayer and aborting shutdown.


However I think that the best solution is to run devil's pie from the 
script instead of sessions, so:

```
#! /bin/bash
sudo -s

#If vmplayer "path/to/VM" launches VM and vmplayer use this command:
vmplayer "path/to/VM" &
#Otherwise remove the previous line, then uncomment the next 2 lines (remove the '#') 
#"path/to/VM" &
#vmplayer &



devilspie &
echo "VM running..."
#The following lines will make sure that the shutdown line is only executed if vm has been closed, so , there's no need to have it configured anymore for that behaviour as it'll just work fine

vmpid=`pidof "path/to/VM"`
wait $vmpid

sudo shutdown -h 0
```Ok, so to recapitulate, put only the script in sessions and for that use this "command" in sessions:
```
xterm -e "/path/to/script"
```-------------------------------
To avoid more frustrations, if the above doesn't work here it is a temporary solution until we can get the script to do what you want:
Notes:
* This solution requires you to manually activate the script but it will automatically shutdown your pc when vmplayer closes
* For this solution you must launch devil's pie and vm and vmplayer from sessions like you did before but without the script
* You are going to launch manually the following script (and I suggest you put it in the desktop so that you don't need to navigate in folders to execute it):

```
#! /bin/bash
sudo -s
echo "Automatic shutdown will occur after VMPlayer is closed, to cancel shutdown please close this window"
vmpid=1
until [ "$vmpid" = "" ];do
vmpid=`pidof vmplayer`
sleep 10 #this is the "lag", it will wait 10 more seconds to check again if vmplayer is still running, the value is in seconds and you can reduce this but don't lower it below 2 or 3 seconds or your pc will be always checking if the condition is true consuming more CPU resources
done
sleep 4 #you'll have 4 seconds to cancel shutdown after vmplayer closes - you can change this value or remove this line entirely to go directly to shutdown
sudo shutdown -h 0
```

---

### Post by Bradleelee on 2008-10-03
So I was able to put it all into one script like you had stated.  It works just like it used to, including not shutting down when VMPlayer does.  At least it does everything else still in one script.  I used the code that you gave me as follows:

```
#! /bin/bash
sudo -s

vmplayer "path/to/VM" &

devilspie &
echo "VM running..."

vmpid=`pidof "path/to/VM"`
wait $vmpid

sudo shutdown -h 0
```

So it seems like everything is working, including Devil's Pie, but for some reason the check to see if the window closes does not work properly. Due to my inexperience I am guessing as to what your code is doing, but it looks like it is looking for a unique identifier for the VM.  Is there a way to do this by just looking for the very next window that closes?

Also, should I look into doing this through FVWM instead? I think there are ways to do this sort of thing through it but I dont know how to use it as of yet.

---

### Post by alberto ferreira on 2008-10-03
I have never used FVWM and I think you would prefer to do this this way because I believe FVWM is more complicated.


Well, I suppose you replaced "path/to/VM" with the real complete path, right?

Then I suggest the following:

replace: vmpid=`pidof "path/to/VM"`
with : vmpid=`pidof vmplayer`


If it still doesn't work try replacing the last line (sudo shutdown....) with one of the following:

sudo shutdown -h now
sudo shutdown now
sudo init 0

If it still doesn't work here it is a script that will create a log so that I can understand what is going on. Run it instead of the older one: 



```
#! /bin/bash
sudo -s
whoami > ~/scriptlog
vmplayer "path/to/VM" &

devilspie &
echo "VM running..."

echo "VM running..." >> ~/scriptlog
vmplayerp=`pidof vmplayer`
vmp=`pidof "path/to/VM"`
echo "Vmplayer pid is:$vmplayerp" >> ~/scriptlog
echo "VM pid is:$vmp" >> ~/scriptlog
echo "Script section check vmpid
" >> ~/scriptlog


vmpid=`pidof "path/to/VM"`
echo "Vmpid state on is:$vmpid" >> ~/scriptlog
echo "Pid vmplayer on:`pidof vmplayer` >> ~/scriptlog 
date >> ~/scriptlog
wait $vmpid
date >> ~/scriptlog
echo "Pid vmplayer off:`pidof vmplayer`" >> ~/scriptlog
echo "Vmpid state off is:$vmpid
Shutdown should have occured after this, log end" >> ~/scriptlog

sudo shutdown -h 0

```Don't forget to replace every "path/to/VM"


Please if it doesn't work use the script that creates the log instead and then a file called scriptlog will be created in your home-folder. Then tell me how the script behaved and also paste the contents of scriptlog in your answer.

Don't give up, I think we're almost done ;)

---

### Post by Bradleelee on 2008-10-06
Thank you again. I will give this a try tonight. Been away for the weekend.

Oh and I did change the path to the correct path.

---

### Post by Bradleelee on 2008-10-07
So I switched out the PID entry like you had asked, and it did not work.  I forgot to do the logging, but will get that done if what I tell you now will change anything.

So basically I thought about it and realized when I first started all of this and tried the initial code of:

```
someprogram && sudo shutdown -h 0
```

I did not know what I was doing or what format I was supposed to have it in etc.  Therefore, I went ahead and edited the code a little to test it out as follows:

```
#! /bin/bash
sudo -s

devilspie &

vmplayer "path/to/VM" && sudo shutdown -h 0
```

And it actually worked. When I close the VM, VMPlayer automatically closes, and then the computer shuts down.  I have no idea if this is a poor way of doing it or if it hurts the OS or not.

---

### Post by alberto ferreira on 2008-10-07
No, it's perfecly safe, **_*CONGRATULATIONS!!!!*_ **:D 

(because "&&" means "and", so, when the first part is done the second is executed.)

But now I'm curious, could you do me a favor?
I'd like to know why it didn't worked, could you just execute manually the script that did the logging and send me the code of the script that creates the log _exactly_ as you used and the log created? 

Thanks, and sorry for having complicated things so much

---

### Post by Bradleelee on 2008-10-09
Sure thing. I will get on that tonight. As long as my brain doesn't forget it.

BTW, thanks a ton for your help.  I could not have done it without you!

---

