---
title: "I cant login in Kubuntu"
date: 2005-11-27
forum: General Help
---

### Post by Shatter_Device on 2005-11-27
Hello, I am still new to linux.  
I had ubuntu, but then I decided to change to Kubuntu( I didnt use a upgrade disc). 
My Login screen looks like a kubuntu screen, but I cant login.
I type my user password  and I get this message:
No write access to '/home/shatterdevice/.ICEauthority' 
KDE is ubable to start.

I tried my root password just to check and no luck and a login failed.

Please help me fix this problem.

Just incase anyone doesnt know how to fix this problem, will I be able to re-install over it, or I do I un-install first, I dont know how to do any of those, I would some help on that.

Ubuntu was my first distro of linux, so I really dont know what to do.

Thank you

---

### Post by cdhotfire on 2005-11-27
[quote=Shatter_Device]Hello, I am still new to linux.  
I had ubuntu, but then I decided to change to Kubuntu( I didnt use a upgrade disc). 
My Login screen looks like a kubuntu screen, but I cant login.
I type my user password  and I get this message:
No write access to '/home/shatterdevice/.ICEauthority' 
KDE is ubable to start.

I tried my root password just to check and no luck and a login failed.

Please help me fix this problem.

Just incase anyone doesnt know how to fix this problem, will I be able to re-install over it, or I do I un-install first, I dont know how to do any of those, I would some help on that.

Ubuntu was my first distro of linux, so I really dont know what to do.

Thank you[/quote] 
Choose to start with terminal only, then do:

```

$ sudo chmod 777 /home/shatterdevice/.ICEauthority

``` 
If that doesn't work, then just delete it, wont affect anything that im aware of.

```

$ sudo rm /home/shatterdevice/.ICEauthority

```

---

### Post by jferrando on 2005-11-27
Try to login from the text terminal <ctrl><alt><f1>, then type your username and password.
Then you can become root with 
$ sudo -s
And change to the directory
# cd /home/userdirectory
And set the permissions properly
# chown username FileName

---

### Post by Shatter_Device on 2005-11-27
*cdhotfire:*

```
$ sudo chmod 777 /home/shatterdevice/.ICEauthority
```
and
```
$ sudo rm /home/shatterdevice/.ICEauthority
```

Nothing happen,  I tried the code again to check, and it said no such file or directory.


*jferrando*

I was able to log in to the text terminal and become root.
But I couldnt change to directory it said:
Bash: cd: /home/userdirectory no such file or directory

Also, what command makes me reboot or go into grub, cause my pc is dual booted, and I have to access the forums by switching into my windows. I keep pressing the on/off button( I forget what its called),I dont think thats healthy for my pc.

---

### Post by cdhotfire on 2005-11-27
?, type in nautilus, and check in your home folder, press crtl+h for hidden things, then look for .ICEauthority.  If its there my first command should work.

---

### Post by Shatter_Device on 2005-11-27
I dont know how to get into nautilus.  I dont think I can access my home folder too cause I cant get pass the sign in part.

---

### Post by cdhotfire on 2005-11-27
[quote=Shatter_Device]I dont know how to get into nautilus. I dont think I can access my home folder too cause I cant get pass the sign in part.[/quote]

Go to terminal only, and type in nautilus.

---

### Post by guice on 2005-11-27
You can log in via console right? cd /home/ and do an ls -l. You should see your home directory. If you don't, something is buggered, but make it anyway: mkdir <yourusername>. chown <youseruser>:<youruser>

Replace <youseruser> with your actual user name.

If you see it, cd into it and do ls -al
You should then see .files including the .ICE file.

---

### Post by Shatter_Device on 2005-11-27
*cdhotfire*

I was able to get into nautilus and go into to my home folder, and check for hidden, but I couldn't find .ICEauthority only X.authority.

*guice*
I think I went into my home directory, but I didnt see .ICE or any .files. I just saw roots and also my friend's username, which I forgot he was there till now.

Well my friend gave me his password, and I was extremely shock  that I was able to login into his and not mine.  When I look at his, his background was ubuntu and I surf around abit on his and saw Gnome.  

Maybe I mess up on installation?

---

### Post by guice on 2005-11-27
. files is dot files. Anything that starts with a dot. If your home directory is there, there should be some. Every file in your home directory aside from '..' should be owned by you (including the '.' directory). Ie; you should see your username and group name by every file when you do: ls -al

---

### Post by cdhotfire on 2005-11-27
[quote=Shatter_Device]*cdhotfire*

I was able to get into nautilus and go into to my home folder, and check for hidden, but I couldn't find .ICEauthority only X.authority.

*guice*
I think I went into my home directory, but I didnt see .ICE or any .files. I just saw roots and also my friend's username, which I forgot he was there till now.

Well my friend gave me his password, and I was extremely shock that I was able to login into his and not mine. When I look at his, his background was ubuntu and I surf around abit on his and saw Gnome. 

Maybe I mess up on installation?[/quote]

If there is no .ICEauthority there shouldnt be a problem.  Do you still get that same message?

Did you check in the right home folder?

---

### Post by guice on 2005-11-27
If there's no .ICEauthority, his home directory ownership and/or permissions might be off (ie; unable to create the .ICEauth file).

---

### Post by cdhotfire on 2005-11-28
[quote=guice]If there's no .ICEauthority, his home directory ownership and/or permissions might be off (ie; unable to create the .ICEauth file).[/quote]

Hmm, did not think of that.:)

But still, seems kind of strange he'd do this unknownly.:confused:

---

### Post by Topsiho on 2005-11-28
I think that during the installation only one user was defined with his password (your friend) and that you and your password were not entered or not entered correctly.

The thing you may have to do is to remove the home directory that you maybe made with mkdir (delete it with rmdir) after deleting all files in it.

Do this in a console (is much the easiest):

cd
(you are now in your friends home directory if you are logged in as your friend)

cd ..
(you are now in the directory /home, which you can verify with by entering pwd)

cd your-name
(if that's the name of the directory you created with mkdir and if you made it while in the home directory. If you made it elsewhere you can continue with adduser, see below the ========== line.

rm *
(This removes all files in it. I presume that you did not make any more directories in it. If you did you should do with them the same first what I tell you to do with your home directory.)

cd ..
(This moves you up to /home again)

rmdir your-name
(Now your homedirectory is gone)

=================

And now comes the part that we add you as a user with your password, so you can log in as yourself with your own password. All things above are only maybe necessary to make sure that all goes well and your home directory does not exist already:

**sudo adduser**
Enter password of your friend's if a password is asked.

Enter your username, followed with Enter (of course)

Your home directory is now created with a lot of standard things in it. That's why it is not OK to create it with mkdir as you were advised to do.

Now you have to have a password, without a password anyone can get at your files which you don't want (hackers too):

**sudo passwd yourname**
You do not need your friend's passwd if you do this within a certain amount of time (I think 15 minutes) after the previous sudo)
You are asked to enter a (your) password twice (you don't see what you enter and the second time is a check)
Now your password is updated succesfully.

Hope that this all succeeds.

As an alternative you can do it with:

K-menu -> System -> Users and groups -> dialog in which you can add new users and their passwords.

But I think that your new home directory must not exist already in this case too.
Anyway you can just try it.

Just see what is in your directory by logging in as your self and do a ls -al in a console. You then can see all files, the hidden ones with a dot in front too, that are in it.

Greetz

Topsiho

---

