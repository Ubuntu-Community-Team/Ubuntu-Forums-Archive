---
title: "Removing unused applications from &quot;Open with Other Applications&quot; list"
date: 2008-09-02
forum: General Help
---

### Post by iron_felix on 2008-09-02
Hey, I recently upgraded to Hardy Heron. Due to this some of the older applications I had are no longer used, yet they still show up in the "Open with Other Application" list when I right click a file and choose that option. Why does that happen and how can I remove those programs from the list?

---

### Post by quibbler on 2008-09-03
> **iron_felix said:**
> Hey, I recently upgraded to Hardy Heron. Due to this some of the older applications I had are no longer used, yet they still show up in the "Open with Other Application" list when I right click a file and choose that option. Why does that happen and how can I remove those programs from the list?
Right click on a file - choose Properities - Open with

select and delete the ones you don't want.

Regards quibbler

---

### Post by mdurham on 2008-09-06
> **quibbler said:**
> Right click on a file - choose Properities - Open with

select and delete the ones you don't want.

Regards quibbler

It may be that you missed the point here quibbler. What the OP wrote was "Open with Other Application", NOT "Properties -> Open with".
My "Open with Other Application" list also has unwanted and duplicate entries that I'd like to remove. I'd also like it sorted into some sane order. At the moment it seems a bit random.
Any help would be appreciated.
Cheers, Mike

---

### Post by brownknight on 2008-09-06
mdurham - quibbler is correct. To remove the other "Open With" options that you dont like, do right click on the on the file > properties > and delete the ones you dont want. Note that the current selected item is the one that shows on top as default open with program. 

On the other note, I dont know how to put them in any sane order.

---

### Post by mc4man on 2008-09-06
Many of the listing for 'open with **other** application' are stored in 
/home/<user name>/.local/share/applications. (Certainly all the ones you've added.
They can be deleted from there.
There may or may not be a corresponding entry in mimeapps.list, doesn't matter if they're left or be very careful removing.

see screen for mine

I would be exercise some care deleting the 'standard' ones ( the ones that have app name and icon, be sure you don't want to use it, but any other ones or duplicates can be easily removed.

Note: I custom named many of them , posting screen to show the idea, not what you may find

---

### Post by mdurham on 2008-09-07
> **brownknight said:**
> mdurham - quibbler is correct. To remove the other "Open With" options that you dont like, do right click on the on the file > properties > and delete the ones you dont want. Note that the current selected item is the one that shows on top as default open with program. 

On the other note, I dont know how to put them in any sane order.

quibbler is correct for "Open With" BUT that is NOT what the question was.
The OP asked about "Open with Other Applications" which is quite different.
Read his Title *carefully* and you will see!
Cheers, Mike

---

### Post by mb_webguy on 2008-09-07
> **mdurham said:**
> quibbler is correct for "Open With" BUT that is NOT what the question was.
The OP asked about "Open with Other Applications" which is quite different.
Read his Title *carefully* and you will see!
Cheers, Mike
If you remove a program from the Open With list in Preferences, it removes it from the Open With (other application) list in the context menu.  The Open With Other Applications list is a different beast, but it's a reasonable mistranslation.

---

### Post by mdurham on 2008-09-07
> **mc4man said:**
> Many of the listing for 'open with **other** application' are stored in 
/home/<user name>/.local/share/applications. (Certainly all the ones you've added.
They can be deleted from there.
There may or may not be a corresponding entry in mimeapps.list, doesn't matter if they're left or be very careful removing.

see screen for mine

I would be exercise some care deleting the 'standard' ones ( the ones that have app name and icon, be sure you don't want to use it, but any other ones or duplicates can be easily removed.

Note: I custom named many of them , posting screen to show the idea, not what you may find

Thanks a lot mc4man, that's exactly what I wanted to know.
Cheers, Mike

---

### Post by mc4man on 2008-09-07
While in the properties -> 'open with' the 'open with other' is what you see from the add button. Anything you 'remove' from the 'open with' can be added right back.

Any custom command is added to the .local.... folder and becomes part of the 'open with other' which then can be added to the 'open with'

Any 'custom command' can also be renamed to differentiate or deleted from .local.....

To rename you use gedit on the icon in .local...... (not r. click rename

whew

---

### Post by mdurham on 2008-09-07
> **mc4man said:**
> While in the properties -> 'open with' the 'open with other' is what you see from the add button. Anything you 'remove' from the 'open with' can be added right back.

Any custom command is added to the .local.... folder and becomes part of the 'open with other' which then can be added to the 'open with'

Any 'custom command' can also be renamed to differentiate or deleted from .local.....

To rename you use gedit on the icon in .local...... (not r. click rename

whew

"whew" indeed!

---

### Post by mc4man on 2008-09-07
it (the .local ....) can become very handy. If you take a close look at screen all of those .desktops become available choices from  - setting the default choice for autorun, the 'normal' r. click open with, and either having autorun set to 'ask me' or holding down shift button on media insert.

Add a few nautilus actions and or nautilus  right click scripts and you can get any app to do anything as far as multimedia whether on media or hdd

---

### Post by iron_felix on 2008-09-09
Hey, thanks guys! That took care of the problem. You are life savers!

---

### Post by efrenefren on 2009-01-27
> **mc4man said:**
> Many of the listing for 'open with **other** application' are stored in 
/home/<user name>/.local/share/applications. (Certainly all the ones you've added.


mc4man, gave the answer to the question.
the other answers were also correct but it's for another question. :)

i thinks this be marked as solved

---

### Post by cobra2150 on 2009-02-26
> **efrenefren said:**
> mc4man, gave the answer to the question.
the other answers were also correct but it's for another question. :)

i thinks this be marked as solved

I was looking for this as well and found the answer entirely by accident when I was looking around for something else.


System --> Preferences --> Main Menu

Then click on the folder on the right marked other, remove the entries that you do not want anymore (This will take them away from the Open With Other Program's List) and then close the dialog and you are done.  Hope that helps.

---

### Post by chaehaih on 2009-02-28
I have similar but an opposite problem. 

I am not happy with transmission and would like to use bittorrent instead. 

when I download link for a torrent, it either asks me to open it with transmission or save it. 

If I save it then right click it, it does not give me choice to open it with bittorrent, as bittorrent is not in the list of programs that I can choose from the "open with" command. 

It is also not shown in user/local/applications. and It's also not shown in preference>mainmenu>..

how can add a program to open with list, that I can not see. 

And yes I have installed bittorrent just now with synaptic package manager.

---

### Post by mc4man on 2009-02-28
> how can add a program to open with list, that I can not see.


If right click 'open with' doesn't show your app then continue to 'Open with Other Application', if it's not listed there then go to 'Use a custom command'

Typically you would just use what would open your app in a terminal though you are free to use additional parameters if needed or desired. (or your custom command can point to a script if need be.

If your using 8.10 the next time you r. click 'open with' you'll see your 'app' listed.
If your using 8.04 then it's always one entry behind, you'll need to repeat the process and pick anything from the list (open with other application) for the previous pick to show up

Basically the same deal with setting a file association - r. click -> properties -> open with, then if needed go  'add' and if needed -> 'Use a custom command'

---

### Post by kennedyvelez on 2010-08-02
> **mc4man said:**
> Many of the listing for 'open with **other** application' are stored in 
/home/<user name>/.local/share/applications. (Certainly all the ones you've added.
They can be deleted from there.
There may or may not be a corresponding entry in mimeapps.list, doesn't matter if they're left or be very careful removing.

see screen for mine

I would be exercise some care deleting the 'standard' ones ( the ones that have app name and icon, be sure you don't want to use it, but any other ones or duplicates can be easily removed.

Note: I custom named many of them , posting screen to show the idea, not what you may find



same problem, solved...

---

