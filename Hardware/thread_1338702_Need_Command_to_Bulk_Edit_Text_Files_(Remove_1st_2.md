---
title: "Need Command to Bulk Edit Text Files (Remove 1st 2 Lines from Each .url File)"
date: 2009-11-26
forum: Hardware
---

### Post by OzzyFrank on 2009-11-26
Hi. I've seen some cool command-line tricks for bulk editing files around, but never really needed them, so never kept any for future reference. I've seen ones that will remove specific characters etc, so gather there has to be a way to delete the first two lines of specified files without opening them.

Basically, in this post [http://ubuntuforums.org/showthread.php?p=8392692#post8392692](http://ubuntuforums.org/showthread.php?p=8392692#post8392692) where I'm trying to get **.url** files (Internet Explorer shortcuts) to open in Firefox, for some reason the trick now no longer works, unless I edit out the first 2 lines (in red in the following example of one of those **.url**s):

[COLOR="Red"][B][DEFAULT]
BASEURL=http://ubuntugenius.wordpress.com/[/COLOR]
[InternetShortcut]
URL=http://ubuntugenius.wordpress.com/
IDList=
IconFile=http://www.gravatar.com/blavatar/b040b12c9e739ace052197f85996bd27?s=16&d=http://s.wordpress.com/favicon.ico
IconIndex=1
[{000214A0-0000-0000-C000-000000000046}]
Prop3=19,2[/B]

So basically I need a command that only edits ***.url**, removes the first 2 lines, then saves each file. I'm sure this is but a trifle to terminal maestros, so would appreciate your advice. Cheers.

---

### Post by lloyd_b on 2009-11-27
You mean like```
sed -i "1,2 d" *.url
```? :D

This will edit all of the *.url files in the current directory, and delete the first two lines.  Note that it does NOT backup the current files, so use with caution.

Lloyd B.

---

### Post by OzzyFrank on 2009-11-27
Thanks Lloyd. **sed** was the one I had seen around but never took notice of (thought the command had cool uses, though I'd never need it). Shouldn't be an issue re no backup, as these would generally be copied from a Windows partition. And too bad if not - they should have used bookmarks like normal people, not that horrid Microsoft .url format with links as files instead of Bookmarks/Favorites menu items, hehe!

---

### Post by GrahamM on 2011-01-17
> **lloyd_b said:**
> You mean like```
sed -i "1,2 d" *.url
```? :D

This will edit all of the *.url files in the current directory, and delete the first two lines.  Note that it does NOT backup the current files, so use with caution.

Lloyd B.

This an old thread, but How would I do this globally for all folders on the Desktop?

---

### Post by montyl on 2011-04-12
Not entirely sure how to go about that without creating symlinks to every file in one place and using the --follow-symlinks option.

And a side note for the next person that hits this one from a Google search:

The -i (in place) option can be followed by an extension to automatically create a backup of the file(s).

```
sed -i "1,2 d" *.url
```becomes

```
sed -ibak "1,2 d" *.url
```leaving you with *.urlbak as the backup files and *.url as the edited ones.

---

### Post by lloyd_b on 2011-04-14
> **montyl said:**
> Not entirely sure how to go about that without creating symlinks to every file in one place and using the --follow-symlinks option.

And a side note for the next person that hits this one from a Google search:

The -i (in place) option can be followed by an extension to automatically create a backup of the file(s).

```
sed -i "1,2 d" *.url
```becomes

```
sed -ibak "1,2 d" *.url
```leaving you with *.urlbak as the backup files and *.url as the edited ones.

The easiest way to handle all files in subdirectories is to use 'find' as a front end for the sed command:```
find /home/user -name "*.url" -exec sed -i "1,2 d" {} \;
```will search for *.url files in /home/user and in any directories beneath it, and run the 'sed' command provided for any matching file found (the "{}" in the command is substituted with the name of the matching file).

Lloyd B.

---

### Post by montyl on 2011-04-17
Nice, Lloyd.  Thanks!

---

