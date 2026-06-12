---
title: "'find' can't use the '-name' option!"
date: 2005-11-10
forum: General Help
---

### Post by syons on 2005-11-10
when I type:
"sudo find / -name 'libjvm.so'"
the terminal says:
"find: WARNING: Hard link count is wrong for /proc: this may be a bug in your filesystem driver.  Automatically turning on find's -noleaf option.  Earlier results may have failed to include directories that should have been searched"
Could anyone tell me is this a bug?Thanks

---

### Post by YoG%*@ on 2005-11-19
hi!

same problem here and yes, it's definitely a bug (there's quite a lot of hits when searching google =)
i found several bug reports like this one: [http://bugs.gentoo.org/show_bug.cgi?id=86031]("http://bugs.gentoo.org/show_bug.cgi?id=86031")
there's a patch listed there, but i can't tell at the moment, if it works/helps...? anyone experiences with it?

hth, mux

---

### Post by m87 on 2005-11-19
[QUOTE=mux]hi!

same problem here and yes, it's definitely a bug (there's quite a lot of hits when searching google =)
i found several bug reports like this one: [http://bugs.gentoo.org/show_bug.cgi?id=86031]("http://bugs.gentoo.org/show_bug.cgi?id=86031")
there's a patch listed there, but i can't tell at the moment, if it works/helps...? anyone experiences with it?

hth, mux[/QUOTE]

i never use find for complex purpose, you can solve basic searches by using find | grep "something"

---

### Post by taurus on 2005-11-19
Not sure about your system but I just ran your command from a terminal (5.10) and didn't get any error message about /proc.  In fact, it returned 

localhost:~/temp:% sudo find / -name 'libjvm.so'
Password:
/opt/j2sdk1.4.2/jre/lib/i386/server/libjvm.so
/opt/j2sdk1.4.2/jre/lib/i386/client/libjvm.so

---

### Post by neels on 2005-11-19
maybe you should not search the root partition then...
If find does not search /proc, it should not hickup, right?

**sudo find /usr /etc /lib -name 'libjvm.so'**

or use locate *(much faster too, but finds only those files that were there when the last **sudo updatedb** was run, which is a daily cronjob by default)*:

**locate libjvm.so**

... also, your command works perfectly on my machine, too.

---

