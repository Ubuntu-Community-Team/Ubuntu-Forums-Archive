---
title: "Openoffice writer top window bar disappeared"
date: 2008-09-19
forum: General Help
---

### Post by cheaptrick on 2008-09-19
the top window bar, the one with the close, maximise, and minise option has disappeared strangely for open office writer.

Spreadsheet and presentation arent affected though

---

### Post by YldGuy on 2008-09-19
> **cheaptrick said:**
> the top window bar, the one with the close, maximise, and minise option has disappeared strangely for open office writer.

Spreadsheet and presentation arent affected though

is it only for writer or any other window? if so try restarting the window manager from compiz.

---

### Post by clarknova on 2008-09-30
> **cheaptrick said:**
> the top window bar, the one with the close, maximise, and minise option has disappeared strangely for open office writer.

Spreadsheet and presentation arent affected though

Same problem here and I'm not using compiz. Or, at least I have desktop effects turned off from the Appearance panel. Affects only OOo writer, i.e., it runs maximised and has no window manager.

Well, it's more than maximised, because my gnome panel disappears. But it's not true full-screen mode, even though it takes the entire screen, because I can still toggle the menus and lower status bar using ctrl-shift-j.

I also tried
```

metacity --replace

```
but it's still behaving the same.

db

---

### Post by dimeotane on 2009-10-08
Similar issue here on a netbook using Ubuntu netbook remix.  
Only the writer window has no bar, and covers my top gnome bar.
No solutions yet?

---

### Post by clarknova on 2009-10-08
I haven't seen this issue in months, probably since upgrading to 8.10 or 9.04.

---

### Post by Hagar Delest on 2009-10-08
Try perhaps the Sun version: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by rootchick on 2009-12-15
I'm having this issue on 8.04 too.  This is in my .xsession-errors:

Window manager warning: Treating resize request of legacy application 0x3a00059 (Untitled1 ) as a fullscreen request

Also, OO presentation & spreadsheet are normal.  It just seems to affect OO writer.

---

### Post by enigmaticubunt on 2012-04-06
I'm running  Ubuntu 10.04 LTS and Office 3.2.0. I fixed this problem by changing a few characters (preserving all settings).

Here's how: edit **Setup.xcu** located in
** /home/**<user name>[B]/.openoffice.org/3/user/registry/data/org/openoffice
[/B](Make a copy of the original file first, of course.)

Look for the section:
  ```
<node oor:name="Factories">
   <node oor:name="com.sun.star.text.TextDocument">
    <prop oor:name="ooSetupFactoryWindowAttributes" oor:type="xs:string">
     <value>340,162,920,875;1;0,0,0,0;</value>
```Change the numbers following **<value>**: the ones shown are the default for my 1200 x 1600 display resolution. If you're running a low resolution, pick some smaller numbers... For example,
```
     <value>100,100,400,300;1;0,0,0,0;</value>
```should get you a small window you can resize.

The last 5 numbers should be as above (**1;0;0;0;0;**). Save, and you're done!


For more, see my post (near the bottom) at:
[http://user.services.openoffice.org/en/forum/viewtopic.php?f=6&t=29277&p=133522](http://user.services.openoffice.org/en/forum/viewtopic.php?f=6&t=29277&p=133522)

---

