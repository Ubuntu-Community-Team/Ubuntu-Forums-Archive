---
title: "Kate wordcount via KDE script - not working"
date: 2005-11-19
forum: General Help
---

### Post by Zelator on 2005-11-19
Kate suits my needs much better than Gedit, but it has no wordcount. I tracked down a KDE script that is supposed to do the job, but it doesn't. I just get a messagebox saying '! Unable to find script &Word Count."'
The script works in two parts in ~/.kde/share/apps/kate 

wordcount.desktop

[Desktop Entry]
Encoding=UTF-8
Name=Word Count
Type=ShellScript/bash
X-KDE-ScriptName=wordcount.sh

and wordcount.sh

#!/bin/bash
case "$1" in kate*) ;;
*) echo "Please call me from Kate" > &2 exit 1;;
esac
doc=`dcop $1 KateDocumentManager activeDocumentNumber`
dcop $1 editinterface#$doc text | wc | { \
   read lines words chars kdialog -- title "words count" \
           --msgbox "<qt><table> <tr><td>Aantal regels:</td>
           <td align=right><b>$lines</b></td></tr>
           <tr><td>Aantal woorden:</td><td align=right><b>$words</b></td></tr>
           <tr><td>Aantal tekens:</td><td align=right><b>$chars</b></td></tr>
           </table></qt>"
   }

wordcount.desktop evidently works up to a point as the messagebox uses whatever I have put in the name field. wordcount.sh is set as executable.
I tried the two scripts suppled with Kate and they both have the same problem. I tried putting the full path name into wordcount.desktop but no go.
Any ideas?

---

### Post by mlomker on 2005-11-19
I spent some time trying to get it to work, but with the same results.  There's either something unique about Kubuntu or their how-to is wrong.

---

### Post by Zelator on 2005-11-22
Doesn't work on Fedora Core 4 KDE desktop either. Unless both distros are incorrectly implementing it, there must be a problem with Kate.

---

### Post by Zelator on 2005-11-23
So I looked in the Kate project Wishlist and voted for a wordcount. The result was that one of the team posted a solution, which I give here:

> Kates 'external tools' feature provides you with a easy way to do this. Here is a very simple implementation, note though that this does not work with non-local files, and that it saves the document if it has changes. The next version (3.0) of kate will allow to pipe text into commands used for external tools. But adding the following to $KDEHOME/share/apps/kate/externaltools would provide you with a command "Tools->External tools->Word count" that will work with local files:&#8221;

[externaltool_Wordcount]
acname=externaltool_Wordcount
cmdname=
command=url=`echo %URL|sed -r 's,^\\w+\\:/+,/,'`\nkdialog --msgbox "Word count for\\n%URL:\\n$(wc -lwm $url|sed -r 's,\\s*(\\w+)\\s+(\\w+)\\s+(\\w+).*,Lines: \\1\\nWords: \\2\\nCharacters: \\3,')"
executable=wc
icon=
mimetypes=
name=Word count
save=1

On FC4, which I am using again as Kubuntu Breezy can't abide my DVD burner, $KDEHOME is empty, but I found externaltools in /usr/share/apps/kate. I expect ~/.kde/share/apps/kate would work as well.
Note that to make it work you have to add &#8220;, externaltool_Wordcount&#8220; to the global list at the top. You can also add a shortcut, I tried Shift+F12 which does not appear to be used for anything else, at least not by me.

---

### Post by mlomker on 2005-11-24
I'm glad that you found a solution!  I tried both locations on Kubuntu as a test and it didn't work for me, but that's okay...it was your question.  :)

---

