---
title: "[SOLVED] Fading  Application"
date: 2008-08-09
forum: General Help
---

### Post by retiree on 2008-08-09
Every time I start Google Maps application it loads and as soon as I take my mouse pointer off the app it closes the app.Is this a compiz setting problem or what? No other application does this. I do have compiz set to fade out the app after moving mouse pointer off of the app, and reappear with mouse over. This not a matter of opacity set wrong either. Is it possible Google Maps needs reinstallation?  Thanks for any suggestions.

---

### Post by tamoneya on 2008-08-09
can you start the app by running it in terminal.  That way we will get some nice error messages to work with.

---

### Post by retiree on 2008-08-09
Thanks for the quick reply.
 I ran it in terminal and got the message "There was an error creating the child process for this terminal"

After looking at the icon launcher properties on the taskbar and the properties on the launcher in google folder they are different. I think this is the problem and I don't know how they got corrupted. I have not changed anything.It could have happened during a update I guess.

Taskbar launcher command: /home/clayton/google-GoogleEarthearth //googleearth %f

Google folder launcher: /home/clayton/google-earth//googleearth %f

I don't know which command is right, so I changed the taskbar launcher to the same as the folder launcher and in ran the app but it did the same thing again, opening up and then closing as soon as the mouse pointer moved off the app. The taskbar launcher looks garbled to me, but that is the way it was when I first looked at it.The last time i ran it there was no problem,but it has been several weeks since i ran it.

I do appreciate the help, Retiree

Edit: Actually I don't have to move the pointer off the app,it will close by itself.

---

### Post by Vivaldi Gloria on 2008-08-09
1) Start a terminal and enter 

```
googleearth
```

What happens? If you get any errors then copy & paste here.

2) Did you install GE using the medibuntu repos?

---

### Post by retiree on 2008-08-10
I did not install with Medibuntu and here is the message from terminal.

clayton@clayton-desktop:~$ googleearth
bash: googleearth: command not found
clayton@clayton-desktop:~$ cd google-earth
clayton@clayton-desktop:~/google-earth$ googleearth
bash: googleearth: command not found
clayton@clayton-desktop:~/google-earth$

---

### Post by Vivaldi Gloria on 2008-08-10
> **retiree said:**
> I did not install with Medibuntu and here is the message from terminal.

clayton@clayton-desktop:~$ googleearth
bash: googleearth: command not found
clayton@clayton-desktop:~$ cd google-earth
clayton@clayton-desktop:~/google-earth$ googleearth
bash: googleearth: command not found
clayton@clayton-desktop:~/google-earth$

So where and how did you install it? 

I suggest you install it using medibuntu repos. Read my posts here:

[http://ubuntuforums.org/showthread.php?t=885260](http://ubuntuforums.org/showthread.php?t=885260)

---

### Post by retiree on 2008-08-10
I reinstalled using synaptic and it opens the app and immediately closes.Do i need to completely uninstall and then reinstall? Could there be some setting in compiz causing this? I don't remember how I first installed it,since it has been a long time.I think I used the Debian package to install originally. It has run flawlessly in the past. I am on Hardy x64 bit. 
 I will read your post and get back later.  Thanks for your time and help.
file:///home/clayton/Desktop/Screenshot.png

---

### Post by Vivaldi Gloria on 2008-08-10
> **retiree said:**
> I reinstalled using synaptic and it opens the app and immediately closes.Do i need to completely uninstall and then reinstall? Could there be some setting in compiz causing this? I don't remember how I first installed it,since it has been a long time.I think I used the Debian package to install originally. It has run flawlessly in the past. I am on Hardy x64 bit. 
 I will read your post and get back later.  Thanks for your time and help.

Try googleearth in a terminal again please. Any errors?

---

### Post by retiree on 2008-08-10
I ran in terminal again and received the same message: command not found
After reinstalling from synaptic it opens and then closes quickly.
I'm headed to Church and it may be awhile before I get back. Thanks again, Retiree

---

### Post by Vivaldi Gloria on 2008-08-10
Please do the following.

1. Right click on the ubuntu symbol (apps menu) and choose edit menus.

2. Find Google Earth in that edit menus program. Right click on Google Earth and choose properties.

3. What does it write in the command box? Copy and paste here.

4. Also copy and paste it in a terminal and report back errors.

I'm also going out btw.

---

### Post by retiree on 2008-08-10
> **Vivaldi Gloria said:**
> Please do the following.

1. Right click on the ubuntu symbol (apps menu) and choose edit menus.

2. Find Google Earth in that edit menus program. Right click on Google Earth and choose properties.

3. What does it write in the command box? Copy and paste here.

4. Also copy and paste it in a terminal and report back errors.

I'm also going out btw.

Properties of command box: /home/clayton/google/-earth//googleearth %f



Terminal:  clayton@clayton-desktop:~$ cd google-earth
clayton@clayton-desktop:~/google-earth$ /home/clayton/google/-earth//googleearth %f
bash: /home/clayton/google/-earth//googleearth: No such file or directory
clayton@clayton-desktop:~/google-earth$

---

### Post by Vivaldi Gloria on 2008-08-10
OK. Let's try this:

1) Start synaptic. Find google earth. Make a note of which version is installed (4.2 or 4.3). Right click and choose completely remove. If it uninstalls properly then proceed with step 2.

2) Delete the google earth folder in your home folder (if it exists). 

3) Delete the .googleearth folder in your home folder (if it exists). Note that the files that start with a dot are hidden and you need to press CTRL+H to see the hidden files.

4) Check if the GE item is still there in the apps menu. If it's still there then start the menu editor and delete it.

5) Start synaptic. Install GE the version 4.3 if you had 4.2 before and install 4.2 if you had 4.3 before. 

6) Start a terminal and give the command

```
googleearth
``` 

and copy and paste the result if you get an error.

7) Also copy and paste the result of the command

```
whereis googleearth
```

---

### Post by retiree on 2008-08-10
Ok I have uninstalled everything and downloaded thru synaptic and got version 5.2 (Debian) on my desktop. What is the terminal command to install it? I have already marked it to allow execute permission.

Synaptic installed it but it is not showing up. I have not been able to find where it installed. I hope I am not confusing you because at this point I am!! Thanks

---

### Post by Vivaldi Gloria on 2008-08-10
> **retiree said:**
> Ok I have uninstalled everything and downloaded thru synaptic and got version 5.2 (Debian) on my desktop. What is the terminal command to install it? I have already marked it to allow execute permission.

Synaptic installed it but it is not showing up. I have not been able to find where it installed. I hope I am not confusing you because at this point I am!! Thanks

There is no GE 5.2 out there. There is 4.2 and 4.3 beta. Where did you get 5.2 from? 

I thought I asked you to install using medibuntu repos but I guess I didn't clearly. Let me quote it from the thread I mentioned above:

-------------------------------------------

GE is available in the medibuntu repos:

[http://www.medibuntu.org/](http://www.medibuntu.org/)

Follow the howto there to add medibuntu to your repo list. If you have ubuntu 8.04 hardy heron then these are the commands:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

Now you can install GE using synaptic:

system menu > admin > synaptic

-------------------------------------------

Do you have problems installing with synaptic? First add medibuntu as mentioned above. Open synaptic, search for GE, right click GE 4.3 and choose install. Then press the check sign to install.

Once you install it you should give the commands in steps 6 and 7 in the above post.

I'm also going to bed now. It's 2am here. Goodnight.

---

### Post by retiree on 2008-08-11
I'm sorry I probably wasted some of your time in your trying to help me.I didn't realize there was such a time frame difference in our post. When you signed off at 2 am, it was 6 pm here,I realized there was a 8 hour difference. It is people like you that keeps Linux alive and growing, and willing to help others. You are to be commended for all of your efforts, and I do sincerely appreciate the help.

BTW I am in the US and my setup of Ubuntu downloads from US servers.That is the reason my version was 5.2, downloaded from synaptic.I did take a look at Medibuntu and I will bookmark it.
After I uninstalled all of GoogleEarth and reinstalled from synaptic it says it installed, but I have not been able to find the folder where it installed to. Terminal search or find file search did not find it either.I do have the file from earth.google.com on my desktop as a .bin file and will try to install from there. Thanks again for the help, Retiree

---

### Post by Vivaldi Gloria on 2008-08-11
> I'm sorry I probably wasted some of your time in your trying to help me.I didn't realize there was such a time frame difference in our post. When you signed off at 2 am, it was 6 pm here,I realized there was a 8 hour difference. It is people like you that keeps Linux alive and growing, and willing to help others. You are to be commended for all of your efforts, and I do sincerely appreciate the help.

No problem. Glad to help. :-)

> BTW I am in the US and my setup of Ubuntu downloads from US servers.That is the reason my version was 5.2, downloaded from synaptic.

OK. I realised what's going on. You're installing this:

[http://packages.ubuntu.com/hardy/googleearth-package](http://packages.ubuntu.com/hardy/googleearth-package)

This is not google earth itself but "utility to automatically build a Debian package of Google Earth". I don't know much about this package. GE is NOT available in synaptic unless you add medibuntu repos.

I suggest you remove everything related to GE, add medibuntu repos and then install GE 4.2 or GE 4.3 using synaptic.

The latest version of GE is 4.3 (beta) even if you live in the US. So don't waste anymore time with that 5.2 thing because it is not GE.

Medibuntu repos is easy to add. Use those commands in a terminal. Then open synaptic, search and install GE 4.3.

---

### Post by retiree on 2008-08-11
Thank you so much for your patience and help!!!:popcorn:
 I did add medibuntu to repositories and downloaded GoogleEarth and it now works great!! I hope you have a Blessed day:KS
Now all I need to do is mark this thread solved. Thanks again, Retiree

---

### Post by Vivaldi Gloria on 2008-08-11
> **retiree said:**
> Thank you so much for your patience and help!!!:popcorn:
 I did add medibuntu to repositories and downloaded GoogleEarth and it now works great!! I hope you have a Blessed day:KS
Now all I need to do is mark this thread solved. Thanks again, Retiree

You're welcome mate. ;)

---

