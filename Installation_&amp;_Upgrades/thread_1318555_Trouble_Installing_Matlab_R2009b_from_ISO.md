---
title: "Trouble Installing Matlab R2009b from ISO"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by tylerthemiler on 2009-11-07
Hey all,

I'm trying to install Matlab R2009b from an iso file. I have it mounted in Gmount and follow the instructions here: [https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB)

The installer successfully initiates, and it accepts my access code, but once it starts trying to actually install I get this error:

"There was an error extracting the archives from MATLAB. This is usually caused by a lack of disk space, or a permissions error (there may be a different installation of MATLAB by a different user), or a missing download archive." 

When I click help it reads:

"There is a problem accessing file on the disk or copying file from the disk to the MATLAB ROOT folder. The 'install' shell script sets environmental variables for accessing the disk on different platforms. Be sure you mounted the disk according to the MATLAB Installation Guide [which doesn't go over how to mount it properly]."

I tried redownloading the iso so that's not the problem and there is plenty of disc space. I don't know what else to try as I am extreamly new to linux. 

Any help would be greatly appreciated! :D

---

### Post by bantaar on 2010-04-15
I am trying to install 32 bit student version of matlab on AMD64 ubuntu 9.10.

I get the same error as the user above with same help notes. I have plenty of disk space, i install as root, I've tried multiple times by removing all files created when starting install script and retrying. I use the -glnx86 flag. I can not find any help to this problem anywhere. This was the only thing I found when searching but saw no answers so I figured I would bump the thread and let you know I have same problem.

---

### Post by bantaar on 2010-04-17
I found two sets of good instructions that I will paste here for the other user (tylerthemiller) with a problem to try.
[http://ubuntuforums.org/showpost.php?p=4285510&postcount=6](http://ubuntuforums.org/showpost.php?p=4285510&postcount=6)
[http://ubuntuforums.org/showpost.php?p=5708408&postcount=6]("http://ubuntuforums.org/showthread.php?t=906667&highlight=matlab+-glnx86")

I followed the instructions from the first link and was able to get further, but then when trying step 6, I would get this error:

[COLOR=DarkOliveGreen]MATLAB:I18n:FailedOpenLcDb - Failed to open the locale database. The MATLAB process default locale is set to "en_US.US-ASCII".
Severe:
Error checking out license
The program '[5707] : Native' has exited with code 1 (0x1).
matthew@matthew-desktop:/usr/local/matlab/bin$ cat: /usr/local/matlab/toolbox/local/classpath.txt: No such file or directory
Unrecognized option: -root
Could not create the Java virtual machine.[/COLOR]

[COLOR=Black]In the second link, step 16, it mentions that if you do not activate before running you will get a JRE error. Perhaps if I activated it would help the error here in this second part of the install. I did not try to activate though because I have decided to return matlab for other reasons. If you have any other questions to try and find a solution just let me know and I will try to help.
I am new here and new to linux, so I am not sure how much details you want.

Edit: Concerning the line about missing file. I CD'd to /usr/local/matlab/toolbox/local and there were a bunch of files, but no classpath.txt. I tried searching online to see if I could download one or just find what is listed in the file but could not find anything. If that is causing a problem for anyone else perhaps they could ask someone with the file to attach it to a post.
[/COLOR]

---

### Post by ashokranade on 2010-05-06
i have installed matlab 2009 on Ubuntu  9.10 - the Karmic Koala according to [https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB) rules given. As i try to launch it from Application<<Programming<<MatlabR2009a it gives " Could not launch 'MATLAB R2009a' and Failed to execute child process "matlab" (No such file or directory). If i try to launch matlab by right click opening a .m file matlab screen flashes but donot go ahead.
Please give some solution to this problem

---

### Post by anfeilong on 2010-06-06
Same msg error here,  Could not launch 'MatlabR2009b'Failed to execute child process "/usr/share/applications/matlab.desktop" (Permission denied), I setup the launcher through the edit menu ... any clues folks

---

### Post by jmblock2 on 2010-06-06
Are you sudoing the install command?

I think I got an error similar to that when I forgot sudo, but its been awhile.

---

### Post by jmblock2 on 2010-06-06
Sorry and for the launching problem, are you using the -desktop flag?

I have 
/opt/matlabR2009b/bin/matlab -desktop
in my launcher

---

### Post by anfeilong on 2010-06-07
yep .... follow all the installation instruction found right here [https://help.ubuntu.com/community/MATLAB/R2009b](https://help.ubuntu.com/community/MATLAB/R2009b), but instead of make my working folder in /usr/local/matlabR2009b I changed it to /home/myname/MatlabR2009b this was the only difference, anyway I'm having some problems launching the program quit sure it is some permission problems

---

