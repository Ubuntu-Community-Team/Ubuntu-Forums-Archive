---
title: "Reverting shell options"
date: 2008-10-12
forum: General Help
---

### Post by thomasyen on 2008-10-12
I've recently made a change to the Bash shell options (forgot what it was). Now whenever I scroll to the end of a manpage or backspace too far (pressing backspace when there are no characters to remove) so that my computer beeps, I automatically log out (probably an X server restart). Any way to revert this?

---

### Post by taladan on 2008-10-12
```
set -o vi
```

Bash has two editing modes: emacs & vi.  If you're in emacs mode then you switch to vi.   However:

```
shopt -o emacs
```

doesn't turn emacs editing mode on in bash, it simply checks and responds to see if you're using emacs mode.  Same with shopt -o vi.  

The default mode in bash in a ubuntu install is emacs, but you can switch between either by using the set -o vi/emacs to test and see which one you prefer.

Tal

---

### Post by taladan on 2008-10-12
As an addendum, and added as a completely separate thought in that vein, you can see what options are set on or off by simply typing:

```
shopt
```

at the command line without any arguments.  Hope this helps.

Tal

---

### Post by thomasyen on 2008-10-12
Thanks for your help. However, I checked my shopt output against another shopt output obtained from a system I know that does not have my problem (restart of X server on backspacing without anything to remove), and it appears that the output is the same. What do I do now?

My shopt output:
```

cdable_vars    	off
cdspell        	off
checkhash      	off
checkwinsize   	on
cmdhist        	on
compat31       	off
dotglob        	off
execfail       	off
expand_aliases 	on
extdebug       	off
extglob        	off
extquote       	on
failglob       	off
force_fignore  	on
gnu_errfmt     	off
histappend     	off
histreedit     	off
histverify     	off
hostcomplete   	on
huponexit      	off
interactive_comments	on
lithist        	off
login_shell    	on
mailwarn       	off
no_empty_cmd_completion	off
nocaseglob     	off
nocasematch    	off
nullglob       	off
progcomp       	on
promptvars     	on
restricted_shell	off
shift_verbose  	off
sourcepath     	on
xpg_echo       	off

```

---

### Post by thomasyen on 2008-10-12
Okay, now I've tried to change the shell options to try and match the original shell options. but I can't have hostcomplete on while having extglob off. It's what the original shell options have. Can anyone help? (Personally, I'm very irritated at having to log back in after hitting backspace one extra time. Tried reinstalling bash, but didn't seem to work.)

---

### Post by thomasyen on 2008-10-12
My system logs. Hopefully someone will be able to tell me what went wrong.
```

Oct 12 20:31:30 thomasyen-desktop gdm[9001]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 (daemon.log)

Oct 12 20:31:30 thomasyen-desktop gdm[9001]: pam_unix(gdm:session): session closed for user thomasyen (auth.log)

Oct 12 20:31:30 thomasyen-desktop gdm[9001]: WARNING: gdm_slave_xioerror_handler: Fatal X error - Restarting :0 
Oct 12 20:31:41 thomasyen-desktop pulseaudio[9624]: pid.c: Stale PID file, overwriting.
Oct 12 20:31:42 thomasyen-desktop hcid[5564]: Default passkey agent (:1.125, /org/bluez/passkey) registered
Oct 12 20:31:42 thomasyen-desktop hcid[5564]: Default authorization agent (:1.125, /org/bluez/auth) registered
Oct 12 20:31:43 thomasyen-desktop NetworkManager: <info>  Updating allowed wireless network lists. 
Oct 12 20:31:43 thomasyen-desktop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored..  (syslog)


```

---

### Post by taladan on 2008-10-12
I don't have any other input for you as I've never encountered anything of this nature.  However, dependent upon how much of a bash history you keep, you can always

```
history|grep shopt
```
and
```
history|grep set
```
to see what all you've done to your bash options (assuming they haven't been pushed out of your history by subsequent commands) and this may lead to someone else spotting an issue...

Sorry I couldn't help more,

Tal

---

### Post by thomasyen on 2008-10-14
It's okay. Not many people (not that I know of) have this problem.
I think I've cleared the shell history before, though, so I'm not sure what you can parse from this.
```
   94  man shopt
   95  shopt
   97  shopt -o vi
   98  shopt -o emacs
  102  shopt +emacs
  103  shopt +o emacs
  104  shopt -o emacs
  105  man shopt
  108  bash -A shopt
  109  shopt -o vim
  110  shopt -o emacs
  111  shopt -o vi
  113  shopt -o
  114  shopt -o > ~/Desktop/shell
  116  shopt
  117  shopt > ~/Desktop/shopt
  120  shopt
  121  shopt -o extglob
  122  shopt -o emacs
  123  shopt
  129  shopt > ~/Desktop/shopt
  131  shopt
  133  shopt
  134  shopt > ~/Desktop/shopt
  136  shopt > ~/Desktop/shopt
  138  shopt > ~/Desktop/shopt
  139  shopt > ~/Desktop/shopt
  142  shopt > ~/Desktop/shopt
  146  shopt
  147  shopt
  149  shopt
  151  shopt
  154  history |grep shopt

```
And there are no entries containing "set".
I recall having this problem before on a Ubuntu Studio (7.10) fresh install. (Well, not exactly fresh; I also installed some other programs. It could be that one of them is messing with the shell, and coincidentally I have that program installed in my current system, but I'm not sure which one.)

---

### Post by taladan on 2008-10-14
I can't see anything that might even remotely be causing that...and thinking about it, I've never heard of a shell option that would cause the behaviour you're talking about.  Here's a question that I didn't think to ask - does this only happen whenever you are using a graphical term or if you hit ALT+F2 and do it, does the error reproduce?

Tal

---

### Post by thomasyen on 2008-10-16
It doesn't happen when I use Alt+F2, only happens when I use Terminal 2.22.1 (GNOME's default terminal emulator).

---

### Post by thomasyen on 2008-10-16
Interesting. I've noticed that *every time* the computer beeps (like when you give some unrecognized command in vim) X server restarts. I'm really stumped. Guess I'll wait till Intrepid comes out and then do a fresh reinstall.

---

