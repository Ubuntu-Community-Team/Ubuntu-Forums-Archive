---
title: "Weird bug with pipes."
date: 2008-08-25
forum: General Help
---

### Post by Alcareru on 2008-08-25
I have this weird bug with pipes. This bug came along with the update from gutsy to hardy heron which I did some time ago (or very soon after it). Sometimes it works and sometimes not. Especially, it usually doesn't work when some application has hung up (it might be that applications easily hung up if piping doesn't work?).. I give some example commands and the results (don't mind about the Finnish. I bet you can imagine what it says..):

timo@timo-desktop:~$ grep
Käyttö: grep [VALITSIN]... HAKUKAAVA [TIEDOSTO]...
Yritä "grep --help" saadaksesi lisäohjeita.

timo@timo-desktop:~$ ps -e | grep firefox
21230 ?        00:39:13 firefox

Ok. Now.. lets continue fooling around in the terminal. Ok now I got it to do it. Here it is (copy-pasted staright from terminal):

timo@timo-desktop:~$ ps -e | grep firefox
21230 ?        00:41:34 firefox
timo@timo-desktop:~$ ps -e | grep firefox
21230 ?        00:41:58 firefox
timo@timo-desktop:~$ ps -e |grep firefox
21230 ?        00:41:58 firefox
timo@timo-desktop:~$ ps -e |*grep firefox
bash: *grep: command not found
timo@timo-desktop:~$ ps -e |*grep firefox
bash: *grep: command not found
timo@timo-desktop:~$ ps -e |*grep firefox
bash: *grep: command not found
timo@timo-desktop:~$ ps -e |*grep firefox
bash: *grep: command not found
timo@timo-desktop:~$ ps -e |*grep firefox
bash: *grep: command not found
timo@timo-desktop:~$ ps -e |*grep firefox
bash: *grep: command not found
timo@timo-desktop:~$ ps -e |*grep firefox
bash: *grep: command not found
timo@timo-desktop:~$ ps -e |*grep firefox
bash: *grep: command not found
timo@timo-desktop:~$ ps -e |*grep firefox
bash: *grep: command not found
timo@timo-desktop:~$ ps -e |grep firefox
21230 ?        00:42:07 firefox
timo@timo-desktop:~$ ps -e |*grep firefox
bash: *grep: command not found
timo@timo-desktop:~$ ps -e |grep firefox
21230 ?        00:42:07 firefox
timo@timo-desktop:~$ ps -e |*grep firefox
bash: *grep: command not found
timo@timo-desktop:~$ ps -e |*grep firefox
bash: *grep: command not found
timo@timo-desktop:~$ ps -e |grep firefox
21230 ?        00:42:08 firefox
timo@timo-desktop:~$ ps -e |grep firefox
21230 ?        00:42:08 firefox
timo@timo-desktop:~$ ps -e |*grep firefox
bash: *grep: command not found
timo@timo-desktop:~$ ps -e |grep firefox
21230 ?        00:42:08 firefox
timo@timo-desktop:~$ ps -e |grep firefox
21230 ?        00:42:08 firefox
timo@timo-desktop:~$ ps -e |grep firefox
21230 ?        00:42:08 firefox
timo@timo-desktop:~$ ps -e |*grep firefox
bash: *grep: command not found
timo@timo-desktop:~$ ps -e |*grep firefox
bash: *grep: command not found
timo@timo-desktop:~$ ps -e |*grep firefox
bash: *grep: command not found
timo@timo-desktop:~$ ps -e |*grep firefox
bash: *grep: command not found
timo@timo-desktop:~$ ls -all |*more
bash: *more: command not found
timo@timo-desktop:~$ ls -all |*less
bash: *less: command not found
timo@timo-desktop:~$ ls -all |less

What the hell? I don't understand. Anyways still at this point grep its self does work because this still works:

ps -e > temporaryfile; grep firefox temporaryfile; rm temporaryfile
21230 ?        00:38:12 firefox

But anyways it kinda sucks to type in:
ps -e > temporaryfile; grep firefox temporaryfile; rm temporaryfile
everytime I'd like to do:
ps -e | grep firefox

This is also something that has happened to me:

timo@timo-desktop:~$ ps -e*| grep firefox
ERROR: Unsupported SysV option.
********* simple selection *********  ********* selection by list *********
-A all processes                      -C by command name
-N negate selection                   -G by real group ID (supports names)
-a all w/ tty except session leaders  -U by real user ID (supports names)
-d all except session leaders         -g by session OR by effective group name
-e all processes                      -p by process ID
T  all processes on this terminal     -s processes in the sessions given
a  all w/ tty, including other users  -t by tty
g  OBSOLETE -- DO NOT USE             -u by effective user ID (supports names)
r  only running processes             U  processes for specified users


x  processes w/o controlling ttys     t  by tty
*********** output format **********  *********** long options ***********
-o,o user-defined  -f full            --Group --User --pid --cols --ppid
-j,j job control   s  signal          --group --user --sid --rows --info
-O,O preloaded -o  v  virtual memory  --cumulative --format --deselect
-l,l long          u  user-oriented   --sort --tty --forest --version
-F   extra full    X  registers       --heading --no-heading --context
                    ********* misc options *********
-V,V  show version      L  list format codes  f  ASCII art forest
-m,m,-L,-T,H  threads   S  children in sum    -y change -l format
-M,Z  security data     c  true command name  -c scheduling class
-w,w  wide output       n  numeric WCHAN,UID  -H process hierarchy


So does anybody have any ideas? Ok I actually have some idea of it myself. The problem probably has something to do with character encoding (I use UTF-8).. because of some weird thing bash (or what?) sometimes thinks that my spaces are asterisks (just like this forum does). But this is a snapshot of the same stuff I just copy-pasted there above. There are no asterisks in it.
[img]http://www.cs.helsinki.fi/u/tglehto/tmp/Kuvakaappaus.png[/img]

Soo.. this is about as far as I can get on my own.. anybody got any suggestions?

---

### Post by jeroenv on 2008-09-09
I got the same problem. Changing or unsetting your LANG environment variable might help, but it might also crash 'command-not-found':

```
jeroen@cerebro:~$ diff fileA fileB | grep "^>" | wc
Sorry, command-not-found has crashed! Please file a bug report at:
https://bugs.launchpad.net/ubuntu/+source/command-not-found
Please include the following information with the report:
unsupported locale setting
Traceback (most recent call last):
  File "/usr/lib/command-not-found", line 19, in <module>
    parser = OptionParser(version = __version__, usage=_("%prog [options] <command-name>"))
  File "/usr/lib/python2.5/gettext.py", line 584, in lgettext
    return ldgettext(_current_domain, message)
  File "/usr/lib/python2.5/gettext.py", line 556, in ldgettext
    return t.lgettext(message)
  File "/usr/lib/python2.5/gettext.py", line 366, in lgettext
    return tmsg.encode(locale.getpreferredencoding())
  File "/usr/lib/python2.5/locale.py", line 514, in getpreferredencoding
    setlocale(LC_CTYPE, "")
  File "/usr/lib/python2.5/locale.py", line 478, in setlocale
    return _setlocale(category, locale)
Error: unsupported locale setting
Python version: 2.5.2 final 0
bash:  wc: opdracht niet gevonden
jeroen@cerebro:~$ 
```

Removing the spaces around the pipe seems a possible work-around as well.

---

### Post by Vivaldi Gloria on 2008-09-09
This is a locale problem. There was a thread about this last week.

---

### Post by Alcareru on 2009-04-27
I just remembered this old thread and thought I'd post the solution to this problem. I think I've figured out what is the problem. The problem is that at least on Finnish keyboard you press Alt Gr when you want to produce the pipe character | and when you quickly type something like ps -e | grep foobar you might accidentally press Alt Gr while you type the spaces. The character produced by Alt Gr and space looks like a regular space, but, obviously, it isn't and there for the command fails. I've upgraded to Jaunty now myself, but I guess this was the problem with hardy too.

So the problem wasn't really a locale problem after all. More like a misspelling and keyboard-layout problem.

I therefor mark this thread as being solved...

EDIT:
Damn, I can't do it properly: [http://ubuntuforums.org/showthread.php?t=1135257](http://ubuntuforums.org/showthread.php?t=1135257)
I try to remember to do it later when the functionality gets reimplemented.

EDIT2:
OMG I actually did remember to mark it solved eventually!

---

