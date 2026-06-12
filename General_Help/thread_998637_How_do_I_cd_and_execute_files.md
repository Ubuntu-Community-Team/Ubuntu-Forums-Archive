---
title: "How do I cd and execute files?"
date: 2008-12-01
forum: General Help
---

### Post by ozguitarplayer on 2008-12-01
Please...I need to learn two things (at the moment)
In the simplest terms.....

1. how do I ....cd to the floder of a text file? 
and,
2. how do I make a file executable

---

### Post by voodooxombie on 2008-12-01
#cd foldername :it should do the work... i am not sure with the problem.
to make file executable change the permission mode using chmod.

#chmod u +x filename : it should allow the user to execute file but depends on file.

# man chmod :for more information.

---

### Post by logos34 on 2008-12-01
you want the parent directory.  Let's say the text file is in 'documents' in your home folder:

cd /home/yourusername/documents

now you're working dir is documents

to make executable:

sudo chmod +x filename

---

### Post by ozguitarplayer on 2008-12-01
thanks logos34, I'll not have a chance to try that for a couple of hours...I'll let you know of my success.

---

### Post by ozguitarplayer on 2008-12-01
hi again, I was able to try sooner than I thought...in both instances I get the response...no such file or directory...
the file is definitely....home/nigel/documents, is there something I might be missing (apart from being a novice with working with terminal?)

---

### Post by /////// on 2008-12-01
Yes your missing the / sign before home, so it should be cd /home/nigel/documents

---

### Post by ozguitarplayer on 2008-12-01
sorry I didn't reply very well, I typed in
cd /home/nigel/documents
I wasn't sure if there was a space between cd & / or not so I tried both ways...same result

---

### Post by nothingspecial on 2008-12-01
Documents starts with a capital D in my home folder. The Terminal is case sensitive. So 

```
cd /home/nigel/Documents
```

---

### Post by ozguitarplayer on 2008-12-01
Iv'e tried every way imaginable, I've tried other ways that are suggest at other sites and the same result. I guess the problem lies elsewhere but not with the typing in terminal....wouldn't know where to look...anyideas??

---

### Post by supersteviobros on 2008-12-01
A few navigational tips:

The terminal is case sensitive. "File," "file," and "fiLE" are different files.

Type "pwd" to see what directory you are currently in.

Type "cd .." to move up one folder.

When you open the terminal, the default directory is /home/yourname

"cd ./foldername" moves you to "foldername" in your current directory. If you were in "/home/yourname" then typing "cd ./Documents" would move you to "/home/yourname/Documents"

"cd ../foldername" moves you to "foldername" one folder back. If you were in "/home/yourname/Documents" then typing "cd ../Pictures" would move you to "/home/yourname/Pictures"

---

### Post by voodooxombie on 2008-12-01
Why don't you try by pressing tab twice to look at the available folders.

---

### Post by 3rdalbum on 2008-12-01
You can drag and drop files into the terminal.

If you want to execute a file in the terminal, then open a terminal window and drag the file into it. Click on the terminal window to bring it back to the front and press Enter.

If you want to "chmod" a file, you can do "chmod u+x " and then drag a file into the terminal.

I haven't used KDE 4, but does Dolphin have an option to "Open Terminal Here" like KDE 3 had? If so, then you could right-click inside a window and choose "Open terminal here", and that way you know that your terminal is inside the correct directory, and you don't have to fiddle around with "cd'ing" and "ls'ing".

---

### Post by ozguitarplayer on 2008-12-01
thanks everyone who is helping, 

I cannot navigate using cd keep getting told 'files don't exist' 

I can drag and drop the files (thanks to the last post) however if I 'chmod +x' I get "Permissiom denied"

Is it just me being daft  or is there a possibility that there is something wrong elsewhere?

---

### Post by nothingspecial on 2008-12-01
Open a new terminal. This will by default be in /home/nigel represented by ~.

Type ```
ls -a
``` to view all the files and directories in your home. When you see the one you want to go to eg documents,
type ```
cd documents
```. The prompt will now say ~/documents$ before the flashing cursor.

Type ```
ls -a
``` again and repeat the process one at a time untill you get where you want to be.

ls on it`s own just shows visible directories whereas ls -a also shows hidden ones (starting with a ".") make sure you include the "." if you want to cd into a hidden directory.

Bear in mind that you can`t cd into a file but you can view it (or listen to it or whatever) with the relevant command.

So to view the file, if it is a text file ```
cat filename.ext
```

To listen to a music file or watch a video file try ```
mplayer filename.ext
```.

If it`s some kind of other file let us know.

Don`t forget to sudo before you chmod if you need to.

---

### Post by ozguitarplayer on 2008-12-01
thanks for that last reply

seems I can do certain functions but not all, though I nearly always get this

nigel@Master:~$ cd documents
bash: cd: documents: No such file or directory

or 

Permission denied if I try chmod

---

### Post by TeXtonyx on 2008-12-01
You have to hit the Enter key after you type a command.
Sometimes it is named the Return key depending on the keyboard.
The notation for this is from the prompt, 

cd /home/nigel/documents <enter> (tap the Enter key)

Now type, ls -la <enter>

Do you see your document listed? You can read it with the cat command.

cat yourdocumentname <enter>

yourdocumentname is discovered by the ls -la <enter> sequence,
which displays all the content of the documents folder.
One has to type filenames exactly as you see them, matching
upper or lower case, letter for letter. Try typing a capital O
and compare it with the zero, 0 , so you can tell the difference.
Sometimes a lower case L, l , will look like the number one, 1

Do you get to the point where you see your document listed
inside the documents folder?

When you give an error report, state at which step it didn't
work which means how far you did get it. 

[http://tldp.org/guides.html](http://tldp.org/guides.html)
Introduction to Linux - A Hands on Guide (free)

available formats:  	

   1. HTML (read online)
   2. HTML (read online, single file, 800k)
   3. HTML (tarred and gzipped package, 1.1M)
   4. PDF (1.6M)

---

### Post by oldos2er on 2008-12-01
> **ozguitarplayer said:**
> 
seems I can do certain functions but not all, though I nearly always get this

nigel@Master:~$ cd documents
bash: cd: documents: No such file or directory
  

 This was already answered. Linux is case-sensitive, so you need to type "cd Documents" or "cd Do[Tab] and let tab do filename completion for you.

---

### Post by ozguitarplayer on 2008-12-01
here's the thing, no matter how or what I type I get....and I must have typed in at least 100 versions.. 

nigel@Master:~$ cd /Documents
bash: cd: /Documents: No such file or directory


or if I drag and drop the file...

nigel@Master:~$ '/home/nigel/Documents/python' 
bash: /home/nigel/Documents/python: Permission denied
nigel@Master:~$ 

is it possible that I am not recognised as the administrator...how can I check this?

---

### Post by oldos2er on 2008-12-01
> **ozguitarplayer said:**
> here's the thing, no matter how or what I type I get....and I must have typed in at least 100 versions.. 

nigel@Master:~$ cd /Documents
bash: cd: /Documents: No such file or directory


or if I drag and drop the file...

nigel@Master:~$ '/home/nigel/Documents/python' 
bash: /home/nigel/Documents/python: Permission denied
nigel@Master:~$ 

is it possible that I am not recognised as the administrator...how can I check this?

 "cd /Documents" will look for Documents from the root directory, so naturally it tells you there's no such thing.

 Try this: cd ~/Documents/python

 Copy and paste it into your terminal.

---

### Post by ozguitarplayer on 2008-12-01
thanks oldos2er
then I get...

nigel@Master:~$ cd ~/Documents/python
bash: cd: /home/nigel/Documents/python: Not a directory
nigel@Master:~$ 

what do you mean by...
"cd /Documents" will look for Documents from the root directory, so naturally it tells you there's no such thing.

I've typed

cd /home/nigel/Documents/python
cd /home/nigel/Documents
cd /home/nigel

always the same result...

---

### Post by oldos2er on 2008-12-01
The "/" in front of the directory name tell the file system to begin searching from root / = root, or the top of the directory tree.

 Would you please open a terminal, and copy and paste the output from this command:
ls

---

### Post by ozguitarplayer on 2008-12-01
hey again oldos2er

I get this...

nigel@Master:~$ ls
autosave                     Documents  GvR       Music     python      Videos
Copy of NoFretGuitarLessons  Downloads  gvr.log   Pictures  Recordings
Desktop                      GNUstep    LimeWire  Public    Templates
nigel@Master:~$

---

### Post by oldos2er on 2008-12-01
Ok. Type:

 cd Doc

then hit Tab. bash should complete the correct name for you (i.e. Documents).

 So you also have either a file or directory named "python" in your home directory, I see. Is this where you're trying to go?

---

### Post by ozguitarplayer on 2008-12-01
ok after I hit Tab I get...

nigel@Master:~$ cd Documents/

is this good? I'm so new to this

yes I have a file named python and I'm trying to make this file executable as a part of a process that will allow me to work with python to learn how to use terminal....so far it's been a long process with very little forward movement :)

---

### Post by oldos2er on 2008-12-01
> **ozguitarplayer said:**
> ok after I hit Tab I get...

nigel@Master:~$ cd Documents/

is this good? I'm so new to this

yes I have a file named python and I'm trying to make this file executable as a part of a process that will allow me to work with python to learn how to use terminal....so far it's been a long process with very little forward movement :)

 Yes, now just hit Enter to go into Documents.

---

### Post by ozguitarplayer on 2008-12-01
you're being very patient, thanks...I then get

nigel@Master:~$ cd Documents/
nigel@Master:~/Documents$

nothing I type after this helps, do I just type python if so...

nigel@Master:~$ cd Documents/
nigel@Master:~/Documents$ python
Python 2.5.2 (r252:60911, Oct  5 2008, 19:24:49)
[GCC 4.3.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>>

---

### Post by oldos2er on 2008-12-01
> **ozguitarplayer said:**
> you're being very patient, thanks...I then get

nigel@Master:~$ cd Documents/
nigel@Master:~/Documents$

nothing I type after this helps, do I just type python if so...

nigel@Master:~$ cd Documents/
nigel@Master:~/Documents$ python
Python 2.5.2 (r252:60911, Oct  5 2008, 19:24:49)
[GCC 4.3.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>>

 Now you're "in" python, which you said is where you wanted be, right?

---

### Post by ozguitarplayer on 2008-12-01
yes, many thanks I appreciate the help

---

### Post by /////// on 2008-12-02
The reason why you get permission denied when you try to chmod the file is because you must add sudo in front of the command. For example in terminal after you get to the directory try "sudo chmod (rest of command)"

---

### Post by oldos2er on 2008-12-02
> **ozguitarplayer said:**
> yes, many thanks I appreciate the help

 Ok, happy programming!

---

