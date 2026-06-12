---
title: "HOWTO: Enabling kate's code folding"
date: 2008-11-01
forum: General Help
---

### Post by kakyoism on 2008-11-01
I've tried a million GUI editors on Linux. Kate is so far the best IMHO. Most essential features that a modern editor should provide such as session management, syntax highlighting, word completion, indentation, and scripting/plug-in system are all decent here, .....except for code folding; I didn't see any of my control-flow foldable yet there is a cold-folding entry in the menu with the collapse/expand grayed out. I used to believe that Linux applications are all incomplete in one way or another, so I didn't bother to check how to make it work until today when I got really confused with a gigantic for-loop.

Google led me to realizing that the cold folding needs to be manually enabled by editing the style XMLs.

Here is how:

On my Ubuntu Hardy, the XMLs are located at /usr/share/apps/katepart/syntax/

Find your targeted language style XML, and find at the end of the file the element general,
add a child element to it:

<folding indentationsensitive="1" />

That's it. You are done. Now fire up your old code and they all become foldable.

---

### Post by Timo Veldt on 2009-08-17
Nice post, follow up question.

The <folding indentationsensitive="1"> line enables folding on an indentation (or tab), but how do I go about things when I want to specifically want to fold a line that starts with a specific string (say "XYZ")?

So:

1st line: abc
2nd line: abc
[INDENT]3rd line: don't fold[/INDENT]
[INDENT]4th line: XYZ (<-- FOLD HERE)[/INDENT]
[INDENT]5th line: don't fold[/INDENT]
[INDENT]6th line: XYZ (<-- FOLD HERE)[/INDENT]

---

### Post by farvardin on 2010-08-03
read [http://kate-editor.org/2005/03/24/writing-a-syntax-highlighting-file/](http://kate-editor.org/2005/03/24/writing-a-syntax-highlighting-file/)

and search for:

# beginRegion starts a code folding block. Default: unset.
# endRegion closes a code folding block. Default: unset.

---

