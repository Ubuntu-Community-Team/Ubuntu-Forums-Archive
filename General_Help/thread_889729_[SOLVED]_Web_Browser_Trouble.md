---
title: "[SOLVED] Web Browser Trouble"
date: 2008-08-14
forum: General Help
---

### Post by brucem91 on 2008-08-14
Help. I just recently switched my main desktop computer to only Ubuntu, though ive been using ubuntu through wubi since november, and I install ubuntu on my sisters laptop, wiping vista in the process(we never used vista on it, I wiped it away on purpose). So, due to  whatever, yesterday I took my desktop and installed ubuntu hardy heron. It worked fine. However, I ran into a little problem as I turned on my computer. When I open firefox, all the text is replaced with underscores. I installed another browser on the system through add/remove and I got the same problem in the other browser. I tried uninstalling and reinstalling firefox via synaptic. Didnt work. I was finally able to get online though, I used a program called wine doors to install opera for wine, its how I am typing this message. But I would really love to go back to firefox. Does anyone know what to do. 
Thanks
Bruce

---

### Post by lukjad on 2008-08-14
Try this. Go to your home folder and create a folder called **Hidden Backups**. Then press Ctrl+h to view the hidden folders and look for the .mozilla one. copy it to the **Hidden Backups** folder and then delete the .mozilla hidden folder. Restart Firefox and tell use what happens.

---

### Post by ndbrown on 2008-08-14
Hello, I've been using Ubuntu solo for about a month, and I have a question that might point to a solution for your problem.  I had a problem with Thunderbird not starting initially, but fixed it.  My problem was in copying my profile directory from Windows XP to Ubuntu.

Go to

Applications -> Accessories -> Terminal

from the menu at the top of your desktop.  In the terminal, type

firefox --safe-mode

and see if that starts in readable form.  If it does, then the problem is your extensions.  You will have to remove any extensions you installed; in Firefox, go to Tools -> Add-ons in the menu.

If this doesn't do the trick, then the problem might be some language issue, like a language not supported, although I don't see how that could be the case.  Go with the safe-mode first, and see if that does the trick.

I've also got a blog, and discuss migrating Firefox/Thunderbird from Windows to Linux in the migrations page.

[http://brownn.wordpress.com/](http://brownn.wordpress.com/)

---

### Post by brucem91 on 2008-08-14
So, both solutions didnt work. Lukjad007's restored firefox as if I just installed it, but the underscoring for letters still keeps happening. Ndbrown, the same errors still happen, so I am not sure.

So because I have been using ubuntu for a while, I have noticed that if I run a program using the terminal to execute it, different messages pop-up. Well, I ran firefox using the terminal, and these are all the messages I got. Firefox did still open by the way.

[QUOTE=Terminal]bruce@bruce-desktop:~$ firefox

(firefox:8480): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial 12'

(firefox:8480): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial 12'

(firefox:8480): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='Arial 12', text='English Hello'

(firefox:8480): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial Bold 9.75'

(firefox:8480): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial Bold 9.75'

(firefox:8480): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='Arial Bold 9.75', text='English Hello'

(firefox:8480): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial 9.75'

(firefox:8480): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial 9.75'

(firefox:8480): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='Arial 9.75', text='English Hello'

(firefox:8480): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial 7.5'

(firefox:8480): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial 7.5'

(firefox:8480): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='Arial 7.5', text='English Hello'

(firefox:8480): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial 0.75'

(firefox:8480): Pango-WARNING **: failed to create cairo scaled font, expect ugly output. the offending font is 'Arial 0.75'

(firefox:8480): Pango-WARNING **: shaping failure, expect ugly output. shape-engine='BasicEngineFc', font='Arial 0.75', text='English Hello'
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)


[/QUOTE]

---

### Post by ndbrown on 2008-08-14
Your error messages might help; try this in the terminal:

sudo apt-get install msttcorefonts

or

sudo apt-get update
sudo apt-get upgrade msttcorefonts

(either install or update, followed by upgrade - try the install first)

It looks like a problem with the Microsoft TrueType fonts (arial is one, I believe).  When you type the above commands, you'll be prompted for you password.

---

### Post by lukjad on 2008-08-14
TO get your Firefox looks back the way you want them got to the home folder, erase the new .mozilla folder and go to your **Hidden Backups** folder and copy it back into the home folder. 

It seems that your msfonts are at fault here.

Go to the terminal and type:
```
sudo apt-get install msttcorefonts
```

Tell up what it says and restart Firefox. Hopefully that's all you need to do.

---

### Post by brucem91 on 2008-08-14
Hello, I finally got firefox to work. Yesterday, when I switched my computer from wubi ubuntu and windows xp to Ubuntu by itself, I had copied all the fonts from C:/Windows/Fonts directory, I had a bunch of various fonts installed from the internet that I wanted to keep. On my sisters ubuntu laptop, I had installed kde and it came with a font installer. I switched that laptop back to gnome, but the installer still worked. I didnt want to have to install kde just to get the font installer, and I couldnt find it in the add/remove programs. So I googled how to install fonts in hardy, and I got this link: [http://ubuntuforums.org/showthread.php?t=736996](http://ubuntuforums.org/showthread.php?t=736996)

Using the directions :

[QUOTE=MRiGnS]How about putting them into /usr/share/fonts

and then using

Code:

sudo fc-cache -f

to refresh the cache.[/QUOTE]

In that folder, there a few subfolders, but I copied all my fonts into just the fonts folder. Then I did the terminal command he wrote, and the fonts worked and yea. But I turned off my computer before going to bed(the computer fan is too loud when I try to sleep. Its not really loud, but when I try to sleep and my room is completly quiet, I can hear the fan and it bothers me. I turned it on this morning, and firefox was doing what my first post was. So to fix it(the sudo commands for upgrading ms core fonts and installing them did nothing because it said msttcorefonts had already been installed) I simply deleted all the fonts I had copied into the folder, and now firefox runs and appears fine.

Thanks

Bruce

---

