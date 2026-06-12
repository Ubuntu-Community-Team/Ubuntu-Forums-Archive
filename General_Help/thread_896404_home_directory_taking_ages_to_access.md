---
title: "home directory taking ages to access"
date: 2008-08-21
forum: General Help
---

### Post by defdre on 2008-08-21
Hi Guys,

I've been using Ubuntu as my primary desktop since Gutsy and am loving Hardy Heron.

However I've had a weird problem pop up in the last week or so. Every time I open nautilus (which defaults to my home dir) it takes at least 20 secs for the files and folders to come up. This always used to be basically instant.

It seems to be some sort issue just in my home dir. I've Googled around but can't seem to find anything similar. Some points:

[LIST]
[*]Clicking in the left panel on "File System" or a network share I have mounted, instantly loads the folder
[*]'ls' in my home dir in a terminal also takes a while to list the items. Although not as long as with nautilus
[*]Firefox's upload file dialog box also takes forever to list the home directory contents
[/LIST]

The only things I have installed recently that I think may possibly effect this are:

[LIST]
[*]Office 2003 and Office 2007 via Wine. I didn't have much success with either.
[*]IEs4Linus (I'm a web developer so I need it to test :-)
[/LIST]

Any idea's what could be going on? I'd really appreciate any suggestions.

Cheers

---

### Post by Too Late on 2008-08-21
Well, I would create a new folder in your home directory, move everything there and see if that makes the home folder work faster. Then I'd move things back to home folder, and try to locate the problematic item(s). After locating the "sick" files/folders it might be an easier case to solve.

edit: I've had the same problem (not so serious, though) and, as I remember, the reason was a big pdf file. I moved it elsewhere and nautilus/home started to work normally. Disabling the thumbnailing feature (or limiting it to small files only) could also be useful sometimes. But I've never had such problems with the ls command.

---

### Post by defdre on 2008-08-21
Thanks for the tip Too Late. I was going to go ahead with this but then had to restart my box this morning (I usually leave it up for weeks / months at a time).

And after that the problem seems to have resolved itself! My home directory is as snappy as ever!

I'll be sure to try your tip if it crops up again.

Thanks anyway.

---

