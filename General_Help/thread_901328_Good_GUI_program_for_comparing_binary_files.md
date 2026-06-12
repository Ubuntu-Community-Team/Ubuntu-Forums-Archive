---
title: "Good GUI program for comparing binary files?"
date: 2008-08-26
forum: General Help
---

### Post by caljohnsmith on 2008-08-26
I need to compare two binary files, and I would like to find a nice GUI program to do this rather than use diff or cmp. I just gave "kompare" a shot, but I don't know how to use it; in the dialog where it says "Here you can enter the files you want to compare", it gives a "source" and "destination", but won't let me choose more than one file. That's entirely counter-intuitive to me, so I guess I must be misunderstanding how to use it; if anyone can let me know how to use Kompare to compare two binary files I would appreciate it. Or if you can let me know of another good GUI compare program, that would be great. 

Thanks in advance.

---

### Post by Sukarn on 2008-12-08
Did you try vbindiff? Its command line based

---

### Post by caljohnsmith on 2008-12-08
Thanks for replying to my 3 month old post; I did find a GUI program that works well, but for the command line, the vbindiff seems to be just the ticket. Thanks for the tip.

---

### Post by dabeatle28 on 2009-01-08
Would you please tell us all wich one is that GUI compare program that works well? I'm also looking for one. I'm on Intrepid trying to find some simple GUI comparison tool for Diff-ext that compare two mp3 just that.

---

### Post by caljohnsmith on 2009-01-08
I haven't really found a GUI binary program that has all the features I would like, but I've been using [AptDiff 1.5]("http://www.aptedit.com/aptdiff.htm") under Wine, and it works well for most cases I'm interested in.

---

### Post by PomCompot on 2009-08-12
Does anybody of you have successfully made diff-ext nautilus extension work? I select my two files, click on compare but nothing happen. Seems though that the bug [https://bugs.launchpad.net/ubuntu/+source/diff-ext/+bug/219121](https://bugs.launchpad.net/ubuntu/+source/diff-ext/+bug/219121) is solved. Any idea?

---

### Post by PomCompot on 2009-08-12
Solved. Have found that you need to configure it to use meld instead of kdiff in Jaunty.

---

