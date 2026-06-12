---
title: "[SOLVED] Text Files will not open in editor"
date: 2008-07-20
forum: General Help
---

### Post by greenco on 2008-07-20
Before converting to Ubuntu 8.04, I made a back up of my important files, that I had stored on Win XP. I did a full install of Ubuntu and when I got to the point I was ready to restore my back ups, I copied them into their folders on the Ubuntu drive. I had "DOC", "XLS", "PFD", "TXT" files and some family pictures. I was able to open and use all of them except for the TEXT files. When I try to open them with "gedit" I get an error message that talks about "gedit has not been able to detect the character coding" and it asks me to "Select a character coding from the menu and try again". I have tried all of them, that I thought might work and nothing does. Does anyone know of what may have caused this, or better yet, a way to correct it.
Thanks

---

### Post by spiderbatdad on 2008-07-20
have you tried opening the text files with vim or nano then copy them into new text files? This is a known compatibility issue between notepad and gedit...not sure what workarounds there are. I have heard of FLOSS for windows, but too late for that in your case it sounds like.

---

### Post by Vivaldi Gloria on 2008-07-20
The quote below is from

[http://tldp.org/LDP/GNU-Linux-Tools-Summary/html/text-filter-tools.html](http://tldp.org/LDP/GNU-Linux-Tools-Summary/html/text-filter-tools.html)

Be careful about the warning. I've never used the commands so I cannot comment on them.

------------------------------------------

**recode**

    Converts text files between various formats including HTML and dozens of different forms of text encodings.

    Use recode -l for a full listing. It can also be used to convert text to and from Windows and UNIX system formats (so you don't get the weird symbols).

**Warning:** By default recode overwrites the input file, use '<' to use recode as a filter only (and to not overwrite the file).

    Examples:
         
    Windows text to UNIX system text:

```
recode ..pc/ file_name
```

    UNIX system text to Windows text without overwriting the original file (and creating a new output file):

```
recode ..pc < file_name > recoded_file
```


**tr**

    (Windows to UNIX system style conversion only). While tr is not specifically designed to convert files from Windows-format to UNIX system format by doing:

```
tr -d '\r' < inputFile.txt > outputFile.txt
```

    The -d switch means to simply delete any occurances of the string. Since we are looking for '\r', carriage returns it will remove any it finds, making the file a UNIX system text file. You can read more about tr over here, Section 11.4.

---

### Post by Pro-reason on 2008-07-20
> **greenco said:**
> I get an error message that talks about "gedit has not been able to detect the character coding" and it asks me to "Select a character coding from the menu and try again".
Thanks

I have had problems due to different ways of encoding characters and line breaks.

Can you print the contents of a text file to the terminal by using the "*cat*" command?  (e.g. *cat addressbook.txt*)

Post one of the files here as an attachment.  I will make it work for you.

---

### Post by greenco on 2008-07-21
Here is one of the files.

Do either of those two editors work with Ubuntu?

Thanks

---

### Post by JagDragon on 2008-07-21
If you run in a terminal
```
cat notworkingfile.txt > newfile.txt
```It should just capture the plain text. Where "notworkingfile.txt" is the one not opening in gedit, and "newfile.txt" is the new file.

---

### Post by Pro-reason on 2008-07-21
> **JagDragon said:**
> If you run in a terminal
```
cat notworkingfile.txt > newfile.txt
```It should just capture the plain text. Where "notworkingfile.txt" is the one not opening in gedit, and "newfile.txt" is the new file.

That assumes that *cat* is able to display the contents of the file in the first place.  

In this case, it isn't.  Running *cat* returns nothing for me.  Opening the file in KWrite gives an error complaining that the file is a binary.  I cannot find any text in it.

P.S. I've just tried to open it in Notepad in XP.  It opens fine, but as a blank file.  How was this file created in the first place?  How was it transferred to the other computer?  (Are we somehow seeing NTFS-compressed files here?)

---

### Post by JagDragon on 2008-07-21
Have you tried opening it with a Hex editor such as bless?
```
sudo apt-get install bless
bless notworkingfile.txt
```

---

### Post by dracayr on 2008-07-21
the file doesn't work with me either...

the file you uploaded is broken: the output of od:

```
0000000 000000 000000 000000 000000 000000 000000 000000 000000
*
0002460 000000
0002462
```

dracayr

---

### Post by Pro-reason on 2008-07-21
> **JagDragon said:**
> Have you tried opening it with a Hex editor such as bless?
```
sudo apt-get install bless
bless notworkingfile.txt
```

Why can't you?

OK, *bless* indicates that it is full of zeros.

Greenco, can you post another example for us?  Are they all this small?  I suspect that all the data has been lost somehow.

---

### Post by dracayr on 2008-07-21
do you still have the backup? try opening a file from the backup media (external hdd, floppy, cd, etc.). If that works, try copying the txt files again (from the terminal with ```
 cp -f /path/to/backup/*.txt /path/to/destination/
``` )

dracayr

---

### Post by JagDragon on 2008-07-21
> **greenco said:**
> Here is one of the files.

Do either of those two editors work with Ubuntu?

Thanks

I opened tht in Windoze and all I got was a notepad file with lots of blank characters :S

---

### Post by greenco on 2008-07-21
Here  are a couple more examples. Most of the files were small diabetic recipes, but I found one that is larger in size. I just noticed that four files came through in a readable format. Go figure!!!

Good file = Aircraft Settings
BAD Larger file = Scenery-Trees

---

### Post by Vivaldi Gloria on 2008-07-21
> **greenco said:**
> Here is one of the files.

I cannot open that text file in windows XP. So there is something wrong with it.

---

### Post by Vivaldi Gloria on 2008-07-21
> **greenco said:**
> Here  are a couple more examples.

Where?

---

### Post by greenco on 2008-07-21
I don't guess the attachment made it. I will try it again. Most of the files are small diabetic recipes.

I noticed that four files made it through in a readable format. 
The file named acft settings is OK
The file named scenery-trees is bad.

Sorry, but I can't get the attachment to work, so I will try again.

---

### Post by greenco on 2008-07-21
Another attempt at attaching the files. I discovered that the other files were too big to attach. Here are two more that should get attached.

The "aircraft-cfg" file is Ok and can be read.
The c210 flights is a bad copy and can not be read.

---

### Post by Vivaldi Gloria on 2008-07-21
> **greenco said:**
> The c210 flights is a bad copy and can not be read.

I can open it neither in windows XP nor in ubuntu.

---

### Post by greenco on 2008-07-21
Thanks for everyone's help!!!
I will consider it hopeless and start collecting the data again. I can tell by the file name, what it was about.

---

