---
title: "Nautilus search files by content"
date: 2008-11-18
forum: General Help
---

### Post by BigJules on 2008-11-18
Am I missing something or is Tracker not yet integrated into the Intrepid Nautilus? According to Help, the Control-F box requires: "Enter characters present in the name or contents of the file or folder you wish to find" - i.e. you can search by content as well as name in the current folder. 

In the absence of filters in the super-minimalist Intrepid Tracker gui this would be an awesome step forward. So how's it done?

---

### Post by happyhamster on 2008-11-18
Tracker search was stripped from nautilus and still is I believe. When it was integrated, people started complaining about a different ctrl-f functionality in nautilus, etc. See for example:
[https://bugs.launchpad.net/nautilus/+bug/150379](https://bugs.launchpad.net/nautilus/+bug/150379)

I really like nautilus' default search tool: it just finds files, in current and child folders, and that's it. I also like the way you can directly move/copy/open the search results. But it would also be great to be able to use some shortcut to do a *local* tracker search instead (for file content).

Anyway, just give me 2 more years or so to get really good at C, and I'll try fixing it myself :D.

---

### Post by BigJules on 2008-11-19
Ah, so it wasn't me. Thanks for the info, HappyHamster. I agree, the Nautilus file search is the best, and fully satisfies. And on my Intrepid, Tracker certainly finds it all by content - the pity of it is that (a) there's no filter to restrict the results to one directory (b) there's no regex capability or whatever to cut out noise in the results. The indexing backend working so well, how about more attention to the front end? Luck with the C!

---

### Post by buixuanduong1983 on 2009-01-19
Hello everybody, I have just finished a new search tool for Linux, called QuickSearch ([http://quicksearch.sourceforge.net/]("http://quicksearch.sourceforge.net/")). The ideal for this new tool is inspired from PDFind (a search tool of PowerDesk package). Among many search tools available nowadays for Linux, I found that all of them index the file system, including file content into a database, this is done when computer is not doing other thing (correct me if I'm wrong). But, normally user only need to search for file name, and they (in most case) only need to search in a specific folder, not all filesystem.

So my SearchTool use a different way: it uses 'ls' command to list content of searched folder, then does the search on that output. This way search speed is very fast (except for the first time it has to make the 'ls' output).

This is the first (pre-beta) of this tool. It is written by Gambas2, and depends on gambas2-runtime package. At this release I only tested it in Ubuntu 8.10. It is still very simple, so I am looking forward for your comment and advise:
- how can I improve it?
- how do you think about it?
- if it is OK then how can I spread it?

Thanks in advance and looking forward to hearing from you.
[http://ubuntuforums.org/showthread.php?t=1042945]("http://ubuntuforums.org/showthread.php?t=1042945")

(I didn't notice about Nautilus search tool before writing this tool. But Nautilus search is good, as well as my tool :-))

---

### Post by BigJules on 2009-01-21
Nice one, Buixuanduong. Shall certainly have it by me for the future, but my requirement really is for a search by content, such as a string in the file, and integrated into Nautilus for convenience. 

Tracker is getting there, and despite a quaint way with numbers on the results, seems to find everything. How I WISH it could filter with regular expressions, find more than one word...

---

