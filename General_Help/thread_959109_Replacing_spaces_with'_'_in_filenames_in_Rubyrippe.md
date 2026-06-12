---
title: "Replacing spaces with'_' in filenames in Rubyripper?"
date: 2008-10-26
forum: General Help
---

### Post by ken300 on 2008-10-26
Hi,

I've just downloaded & tried out Rubyripper to rip to mp3. I've already got loads of cds ripped to mp3 with all of the spaces in their file names & folder structure replaced by '_' (ie: ./Music/Green_Day/American_Idiot/01_American_Idiot.mp3).

There doesn't seem to be an option in the Rubyripper GUI to do this (it stays as: ./Music/Green Day/American Idiot/01_American Idiot.mp3). Is there a way of getting it to replace the spaces with '_' so that the Rubyripper mp3s match my existing ones, a line to add to the text settings file maybe??

Thanks!

---

### Post by Pro-reason on 2008-10-26
I don't know anything about the program that you are using, but I know how to fix filenames.

To change all spaces to underscores in all files in the current directory:

```

rename "s/_/ /g" *

```

Do “info rename” to know more.

---

### Post by geirha on 2008-10-26
[tagtool](apt://tagtool) is a gui tool that can rename files based on mp3-tags and set mp3-tags based on filenames.

---

### Post by vanadium on 2008-10-26
There is indeed currently no option in Rubyripper to replace spaces. You will indeed need to do the renaming afterwards. You have already got two good tips. Easytag is yet another option. For the rename option, the command should read

```
rename "s/\ /_/g" *
```

You can do a "test" run adding the -n option:

```
rename -n "s/\ /_/g" *
```

Rubyripper is young software: probably the feature will be added at some time.

---

### Post by ken300 on 2008-10-26
Thanks for all your responses!

I'm using 'abcde' at the moment & have it setup using sed & tr commands in the abcde.conf file to give the structure I want. I was just impressed with rubyripper this morning & wondered if there was some way of tweaking it to work how my abcde setup does.

My current 'abcde' method is nice & simple & I don't fancy the idea of adding an extra stage by editing the tags separately, I guess I'll be sticking with abcde for now (but I'll keep an eye on rubyripper)!

Thanks again!

---

### Post by Pro-reason on 2008-10-26
> **vanadium said:**
> For the rename option, the command should read

```
rename "s/\ /_/g" *
```

The quotation marks around the arguments mean that the space doesn't need to be escaped with a backslash.  It'll work either way.

Doing a trial run is a good idea, though.

---

### Post by gbcox on 2009-01-31
> **ken300 said:**
> Hi,

I've just downloaded & tried out Rubyripper to rip to mp3. I've already got loads of cds ripped to mp3 with all of the spaces in their file names & folder structure replaced by '_' (ie: ./Music/Green_Day/American_Idiot/01_American_Idiot.mp3).


I submitted an enhancement request here:
[http://code.google.com/p/rubyripper/issues/detail?id=274](http://code.google.com/p/rubyripper/issues/detail?id=274)

The author was kind enough to provide a patch, but doesn't believe this is a popular option.  If you want to have it permanently included in the application, add a comment to the record.

---

### Post by Piraja on 2009-03-04
Thank you for this thread. I had exactly the same question as ken300; I also found the issue at the Google Code page and added a comment before I read this thread. I definitely agree with ken300 on the fact that changing the files names afterwards (with e.g. Thunar's Bulk Rename feature, which is a very good GUI tool, by the way) is an extra step we don't want. The naming policy is for me the only setback with Rubyripper CLI so far, after installing it today.

I downloaded the patch provided at [the maintainer's GC site](http://code.google.com/p/rubyripper/issues/detail?id=274) and actually added two extra lines into it (in [COLOR="Red"]red[/COLOR] type): **[LATER EDIT: I'm an idiot. See Geirha's post below!]**
```
--- ../rubyripper/rr_lib.rb	2009-01-29 23:40:14.000000000 +0100
+++ rr_lib.rb	2009-01-31 10:38:17.000000000 +0100
@@ -113,6 +113,8 @@
 		var.gsub!('[', '-') #replace the ' [ ' with a ' - '
 		var.gsub!(']', '-') #replace the ' ] ' with a ' - '
 		[COLOR="Red"]var.gsub!('(', '-') #replace the ' ( ' with a ' - ' #line added by Piraja
 		var.gsub!(')', '_') #replace the ' ) ' with a ' _ ' #line added by Piraja[/COLOR]
 		var.gsub!('"', '') #Add a slash before the double quote chars, otherwise the shell will complain
+		var.gsub!(' ', '_') # Replace spaces with underscores
+		var.downcase! # No capitals allowed
 	else
 		var.gsub!('"', '\"') #Add a slash before the double quote chars, otherwise the shell will complain
 	end
```
Now, as I'm an ignoramus in regard of applying a patch, my question is at which directory should I add it? Here's a list of all the Rubyripper folders (also the irrelevant):
```
./
usr/
usr/share/
usr/share/applications/
usr/share/applications/rubyripper.desktop
usr/share/locale/
usr/share/locale/es/
usr/share/locale/es/LC_MESSAGES/
usr/share/locale/es/LC_MESSAGES/rubyripper.mo
usr/share/locale/nl/
usr/share/locale/nl/LC_MESSAGES/
usr/share/locale/nl/LC_MESSAGES/rubyripper.mo
usr/share/locale/se/
usr/share/locale/se/LC_MESSAGES/
usr/share/locale/se/LC_MESSAGES/rubyripper.mo
usr/share/locale/hu/
usr/share/locale/hu/LC_MESSAGES/
usr/share/locale/hu/LC_MESSAGES/rubyripper.mo
usr/share/locale/de/
usr/share/locale/de/LC_MESSAGES/
usr/share/locale/de/LC_MESSAGES/rubyripper.mo
usr/share/locale/ru/
usr/share/locale/ru/LC_MESSAGES/
usr/share/locale/ru/LC_MESSAGES/rubyripper.mo
usr/share/locale/fr/
usr/share/locale/fr/LC_MESSAGES/
usr/share/locale/fr/LC_MESSAGES/rubyripper.mo
usr/share/icons/
usr/share/icons/hicolor/
usr/share/icons/hicolor/128x128/
usr/share/icons/hicolor/128x128/apps/
usr/share/icons/hicolor/128x128/apps/rubyripper.png
usr/share/doc/
usr/share/doc/rubyripper/
usr/share/doc/rubyripper/README.gz
usr/share/doc/rubyripper/GPL-3.txt.gz
usr/share/doc/rubyripper/changelog.Debian.gz
usr/share/doc/rubyripper/copyright
usr/share/pixmaps/
usr/share/pixmaps/rubyripper.png
usr/local/
usr/local/lib/
usr/local/lib/site_ruby/
usr/local/lib/site_ruby/1.8/
usr/local/lib/site_ruby/1.8/rr_lib.rb
usr/bin/
usr/bin/rrip_gui
usr/bin/rrip_cli
```
So, is it /usr/bin/ or what?

All you ever wanted to ask about applying a patch but were too embarassed to ask...

---

### Post by geirha on 2009-03-04
Those lines you added to the patch should be removed from the patch. The patch won't work with those two added lines.

The (original) patch basically says. In the file rr_lib.rb, go to line 113 where you should see the following six lines.
```

		var.gsub!('[', '(') #replace the ' [ ' with a ' ( '
		var.gsub!(']', ')') #replace the ' ] ' with a ' ) '
		var.gsub!('"', '') #Add a slash before the double quote chars, otherwise the shell will complain
	else
		var.gsub!('"', '\"') #Add a slash before the double quote chars, otherwise the shell will complain
	end

```
In the middle of those lines, add the following two lines:
```

		var.gsub!(' ', '_') # Replace spaces with underscores
		var.downcase! # No capitals allowed

```
+ in front of a line means it should be added, - means it should be removed, and three lines of context before and after are used to identify the correct place. So it doesn't necessarily have to start at line [COLOR="Blue"]113[/COLOR] as the patch says```
@@ -[COLOR="Blue"]113[/COLOR],6 +113,8 @@
``` If it is a few lines before or after, it will still find the correct place, and give you a message that it succeded with a little fuzz.

To patch rr_lib.rb with patch.diff, try
```
patch /path/to/rr_lib.rb < patch.diff
```

If you add a + in front of your two extra lines, it may work, but I recommend you just edit the file manually, browse down to around line 113, and add those lines.

---

### Post by Piraja on 2009-03-04
Thanks for the quick reply! Just before I noticed your post, I realized that the patch itself points the right directory at its first line: 

usr/local/lib/site_ruby/1.8/rr_lib.rb

Good of you to post so quickly, otherwise I would have tried my stupid "enhanced version" of the patch and wondered why it doesn't work... You see, I'm a bit impatient *bricoleur*...

**P.S.** Thank you again, I reread your post carefully. It is very clear and informative, taught me many things on just a few lines. I'll try your suggestions and probably post back in an hour or so... **[Or just edit and confirm. It works as expected.]**

---

### Post by Piraja on 2009-03-04
Wow, I applied my first patch!

There's a funny little detail on lines 116 
```

var.gsub!(' ', '_') # Replace spaces with underscores

```
and line 122 of the newly patched file:
```


	var.gsub!('_', ' ') # replace any underscores with spaces, some freedb info got underscores instead of spaces

```
This won't change the newly created underscores back into spaces, only the underscores in freedb info into spaces, I guess... However, that does not seem like a good idea to me, for fairly obvious reasons. So maybe I'll just remove the line and report back to the maintainer?

---

### Post by geirha on 2009-03-04
I haven't seen the code, but I'm guessing that maybe line 122 is changing the tags (metadata), and not the actual filename..?

---

### Post by Piraja on 2009-03-04
> **geirha said:**
> I haven't seen the code, but I'm guessing that maybe line 122 is changing the tags (metadata), and not the actual filename..?
Oh yes, I guess that must be so, since it is a question of freedb info — they provide tags and not filenames, of course! Thanks for clearing my confused little brain a bit on this one, too.

---

