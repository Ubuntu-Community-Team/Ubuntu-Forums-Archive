---
title: "how can i get a command to execute after X but before GDM?"
date: 2008-07-10
forum: General Help
---

### Post by Darth_tater on 2008-07-10
GO TO PAGE 3.

IGNORE BELOW
------------------------------
ORIGINAL POST


i need to start up a VNC server on this machine... i have a working command that supports encryption and authorization, but i must login to the machine locally first THEN run the command, then use VNC.

how do i make an /etc/init.d/ start up entry so that my command will be executed just after X gets loaded (but before GDM)


--- thanks!

---

### Post by MasterXandrex on 2008-07-10
As far as creating your init script you would write it and then place it into /etc/init.d and the symbolically link it to the proper runlevels (/etc/rc2.d, /etc/rc4.d, /etc/rc5.d...) using a number that would put it in the propper order.

In other words, after you write and oplace your script in init.d you would link it thusly:
```

cd /etc/rc2.d
ln -s ../init.d/script S21script

```

"S21" would be replaced with the proper lettering for the order you want to achieve -- they're started alphabetically. 

However, I don't believe that you can do that. In Ubuntu, as I understand it, the XServer is started by GDM -- I could be wrong as I've not actually dug into it, but experientially that seems to be it. 

Sorry I couldn't help any more, but you didn't actually say what you were wanting to do. If you can provide more information I may be able to help more.


Xan

---

### Post by Darth_tater on 2008-07-10
Well, I want to have a VNC server running on this machine.  As it is, x11VNC is set up to work on display :0.

The problem is, that I have no way of launching this command unless I login physically at the machine or over SSH.  This machine needs to be FULLY accessible via remote for VNC&#8230; SSH wont always be an option to get VNC up and running.

My only option is to have the VNC server start up before the user sees the GDM login screen&#8230; that way, a user can login and use the box on display 0 locally and/or remotely.  Thus, I NEED the command to be executed before the user sees the GDM login screen.  99.9% of the time, this machine will be accessed remotely, the only time it will be accessed locally is if there is some serious problem...

&#61550;	Hopefully that will help clear up any confusion&#8230; I wrote my first post in a hurry.

---

### Post by MasterXandrex on 2008-07-10
Ok, I have an idea, but it will require some tweaking and reading. I use an open source solution called Synergy (great program!) that allows you to use the same keyboard and mouse on two computers without a KVM and it has to be started by the display manager (GDM).

[http://synergy2.sourceforge.net/index.html]("http://synergy2.sourceforge.net/index.html")

I believe you can use the same method that I do for Synergy to start your VNC server.

There is a config file, /etc/gdm/PreSession/Default, that GDM runs before login. If you have it run your script (just put it at the top or bottom of the file) if should start VNC as soon as GDM loads.

One thing you want to make sure of is that if you restart gdm it doesn't get started twice, so make sure to kill it before you start it and sleep for a second or two.

Let me know if you need clarification or further help,

Xan

---

### Post by krunge on 2008-07-10
> **Darth_tater said:**
> i need to start up a VNC server on this machine... i have a working command that supports encryption and authorization, but i must login to the machine locally first THEN run the command, then use VNC.

how do i make an /etc/init.d/ start up entry so that my command will be executed just after X gets loaded (but before GDM)
Have a look here

[http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager]("http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager") 

under the description "Continuously".

---

### Post by Darth_tater on 2008-07-10
Nope... something isn&#8217;t working.  The VNC server will not start by its self&#8230; I am not sure why.

Once the computer gets to GDM and I cannot connect via VNC, I start up my ssh client and run the following command 
> sudo x11vnc -display :0 -bg -usepw -auth /var/lib/gdm/:0.Xauth -forever

I can then login over VNC.  as soon as i login, my connection is killed off, and i have to restart the connection.  As soon as i restart the connection (and server via SSH) i can use my desktop as i normally would.

---

### Post by Darth_tater on 2008-07-11
> **UbuntuUser3859 said:**
> .

There is a config file, /etc/gdm/PreSession/Default, that GDM runs before login. If you have it run your script (just put it at the top or bottom of the file) if should start VNC as soon as GDM loads.

Xan


are the commands in that file executed with root powers?  if not, the sudo appended to my command wont work...and the vnc xerver will fail to start.

that could explain why it isin't starting.

---

### Post by MasterXandrex on 2008-07-11
I'm not entirely sure what permissions the commands are issued as. I know that anything post-login is run as the logging in user.

The link that Krunge posted seems to have a great deal of information for your software along the same lines as I mentioned, I would look there.


Xan

---

### Post by Darth_tater on 2008-07-11
Thanks for all your help, but I still haven’t managed to get it fully working.
I still have to start the session manually (over SSH), but I am no longer kicked out when I login… I can keep my current session running!
I guess the next thing for me to do would be to look at how init.d works…. That should solve my problem.

This is what my /etc/gdm/Init/Default file looks like :

```
#!/bin/sh
# Stolen from the debian kdm setup, aren't I sneaky
# Plus a lot of fun stuff added
#  -George

PATH=/usr/bin:$PATH
OLD_IFS=$IFS

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
    if test -x "$dir/$COMMAND" ; then
      if test "x$OUTPUT" = "x" ; then
        OUTPUT="$dir/$COMMAND"
      fi
    fi
  done
  IFS=$OLD_IFS 
  echo "$OUTPUT"
}

sysresources=/etc/X11/Xresources

# merge in defaults
if [ -f "$sysresources" ]; then
    xrdb -merge "$sysresources"
fi

sysmodmap=/etc/X11/Xmodmap

XMODMAP=`gdmwhich xmodmap`
if [ x$XMODMAP != x ] ; then
  if [ x$GDM_PARENT_DISPLAY = x ]; then
    if [ -f $sysmodmap ]; then
      $XMODMAP $sysmodmap
    fi
  else
    ( DISPLAY=$GDM_PARENT_DISPLAY XAUTHORITY=$GDM_PARENT_XAUTHORITY $XMODMAP -pke ) | $XMODMAP -
  fi

  #
  # Switch Sun's Alt and Meta mod mappings
  #

  UNAME=`gdmwhich uname`
  PROCESSOR=`$UNAME -p`
  if [ x$PROCESSOR = xsparc ]; then
    if $XMODMAP | /usr/bin/grep mod4 | /usr/bin/grep Alt > /dev/null 2>/dev/null
    then
      $XMODMAP -e "clear Mod1" \
               -e "clear Mod4" \
               -e "add Mod1 = Alt_L" \
               -e "add Mod1 = Alt_R" \
               -e "add Mod4 = Meta_L" \
               -e "add Mod4 = Meta_R"
    fi
  fi
fi

SETXKBMAP=`gdmwhich setxkbmap`
if [ x$SETXKBMAP != x ] ; then
  # FIXME: is this all right?  Is this completely on crack?
  # What this does is move the xkb configuration from the GDM_PARENT_DISPLAY
  # FIXME: This should be done in code.  Or there must be an easier way ...
  if [ -n "$GDM_PARENT_DISPLAY" ]; then
    XKBSETUP=`( DISPLAY=$GDM_PARENT_DISPLAY XAUTHORITY=$GDM_PARENT_XAUTHORITY $SETXKBMAP -v )`
    if [ -n "$XKBSETUP" ]; then
      XKBKEYMAP=`echo "$XKBSETUP" | grep '^keymap' | awk '{ print $2 }'`
      XKBTYPES=`echo "$XKBSETUP" | grep '^types' | awk '{ print $2 }'`
      XKBCOMPAT=`echo "$XKBSETUP" | grep '^compat' | awk '{ print $2 }'`
      XKBSYMBOLS=`echo "$XKBSETUP" | grep '^symbols' | awk '{ print $2 }'`
      XKBGEOMETRY=`echo "$XKBSETUP" | grep '^geometry' | awk '{ print $2 }'`
      if [ -n "$XKBKEYMAP" ]; then
        $SETXKBMAP -keymap "$XKBKEYMAP"
      elif [ -n "$XKBTYPES" -a -n "$XKBCOMPAT" -a -n "$XKBSYMBOLS" -a -n "$XKBGEOMETRY" ]; then
        $SETXKBMAP -types "$XKBTYPES" -compat "$XKBCOMPAT" -symbols "$XKBSYMBOLS" -geometry "$XKBGEOMETRY"
      elif [ -n "$XKBTYPES" -a -n "$XKBCOMPAT" -a -n "$XKBSYMBOLS" ]; then
        $SETXKBMAP -types "$XKBTYPES" -compat "$XKBCOMPAT" -symbols "$XKBSYMBOLS"
      elif [ -n "$XKBSYMBOLS" ]; then
        $SETXKBMAP -symbols "$XKBSYMBOLS"
      fi
    fi
  fi
fi
# launch X11VNC
sudo /usr/bin/x11vnc -display :0 -bg -usepw -auth /var/lib/gdm/:0.Xauth -o /var/log/x11vnc.log -q  
exit 0

```
Ths is what my /etc/gdm/PreSession/Default file looks like: 

```
#!/bin/sh
#
# Note that output goes into the .xsession-errors file for easy debugging
#
PATH="/usr/bin:$PATH:/bin:/usr/bin"
OLD_IFS=$IFS

gdmwhich () {
  COMMAND="$1"
  OUTPUT=
  IFS=:
  for dir in $PATH
  do
    if test -x "$dir/$COMMAND" ; then
      if test "x$OUTPUT" = "x" ; then
        OUTPUT="$dir/$COMMAND"
      fi
    fi
  done
  IFS=$OLD_IFS 
  echo "$OUTPUT"
}

# Set background color
XSETROOT=`gdmwhich xsetroot`
if [ "x$XSETROOT" != "x" ] ; then

	CHECKBACKCOLOR="OK"
	if [ "x$GDM_GREETER_TYPE" = "xTHEMED" ]; then
		BACKCOLOR=`gdmflexiserver --command="GET_CONFIG greeter/GraphicalThemedColor $DISPLAY"`

		CHECKBACKCOLOR=`echo $BACKCOLOR | sed 's/^\([^ ]*\) .*$/\1/'`
		if [ "x$CHECKBACKCOLOR" = "xOK" ]; then
			BACKCOLOR=`echo $BACKCOLOR | sed 's/^.* \(.*\)$/\1/'`
		else
			BACKCOLOR=""
		fi
	fi

	# If we tried to load the themed backgroundcolor, but failed, then try loading plain color
	if [ "x$CHECKBACKCOLOR" != "xOK" ] || [ "x$GDM_GREETER_TYPE" = "xPLAIN" ]; then

		# Background type can be 0=None, 1=Image & Color, 2=Color, or 3=Image 
		BACKTYPE=`gdmflexiserver --command="GET_CONFIG greeter/BackgroundType $DISPLAY"`

		# Skip if background type does not include a color
		if [ "x$BACKTYPE" = "xOK 1" ] || [ "x$BACKTYPE" = "xOK 2" ]; then
			BACKCOLOR=`gdmflexiserver --command="GET_CONFIG greeter/BackgroundColor $DISPLAY"`

			CHECKBACKCOLOR=`echo $BACKCOLOR | sed 's/^\([^ ]*\) .*$/\1/'`
			if [ "x$CHECKBACKCOLOR" = "xOK" ]; then
				BACKCOLOR=`echo $BACKCOLOR | sed 's/^.* \(.*\)$/\1/'`
			else
				BACKCOLOR=""
			fi
		fi
	fi

	# Default value
 	if [ "x$BACKCOLOR" = "x" ]; then
 		BACKCOLOR="#76848F"
 	fi

	"$XSETROOT" -cursor_name left_ptr -solid "$BACKCOLOR"
fi

# launch x11
sudo /usr/bin/x11vnc -display :0 -bg -usepw -auth /var/lib/gdm/:0.Xauth -o /var/log/x11vnc.log -q   
exit 0

``` 
Any ideas why the command isint launching?

---

### Post by MasterXandrex on 2008-07-11
Don't use the sudo command in the script. If it's ran as root it's not needed and otherwise the user has to enter a password.

---

### Post by Darth_tater on 2008-07-11
nope.

removing sudo didn't work.

---

### Post by MasterXandrex on 2008-07-11
When you run the command from the terminal, is there any additional output or input. Is it simply that command?

The only other thing that I can think of is that the user that is running the command from GDM does not have sufficient privileges. 

I'm going to check what user it's running as and I'll post my results here.


Xan

---

### Post by MasterXandrex on 2008-07-11
OK, just checked. It runs as root.

All I did was put this: 
```

whoami >> /home/user/xandrex

```

it displayed root.

I'll try to think about this a little more and see if I have any epiphanies.


Xan

---

### Post by Darth_tater on 2008-07-12
I currently don't have access to the machine (it was moved to its remote site), but i can tell you that when i ran the command with the -q (quiet) flag the only output was one line that looked a lot like this:

PORT=5900

-- i don't think that specific output would cause any problems... it would be the last command in the file before 'exit'.

When my connection to the machine gets restored, i will VNC back into the machine (when i left it, the VNC server was running) and make sure that the login window properties are as they should be.  I had to modify them temporarily to solve a different login issue, but i believe i restored them to defaults after the other issue had been fixed. 



-- thanks for sticking w/ me on this issue.

---

### Post by krunge on 2008-07-13
> 
```

sudo /usr/bin/x11vnc -display :0 -bg -usepw -auth /var/lib/gdm/:0.Xauth -o /var/log/x11vnc.log -q   
exit 0

``` 


When running from /etc/gdm/Init/Default:

You don't need the "sudo"

You don't need "-display :0"

You don't need "-auth /var/lib/gdm/:0.Xauth"

You shouldn't use "-q" because you want info to be printed to the logfile /var/log/x11vnc.log.

I suggest getting rid of them. See the link I posted for you a few days ago.  It shows how to do it.

---

### Post by Darth_tater on 2008-07-13
> **krunge said:**
> When running from /etc/gdm/Init/Default:

You don't need the "sudo"

You don't need "-display :0"

You don't need "-auth /var/lib/gdm/:0.Xauth"

You shouldn't use "-q" because you want info to be printed to the logfile /var/log/x11vnc.log.

I suggest getting rid of them. See the link I posted for you a few days ago.  It shows how to do it.


the link you posted specifically states that i DO need the -auth /var/lib... argument.

as soon as the ISP providing service to the remote machine can get the connection restored, i will SSH in and try your recommendations out.

---

### Post by krunge on 2008-07-13
> **Darth_tater said:**
> the link you posted specifically states that i DO need the -auth /var/lib... argument.


No, I said use the section marked "Continously" in that FAQ (I think you are referring to the section marked "One time only").

Also, I am pretty sure you will  need to do the KillInitClients=false described in that FAQ ([http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager]("http://www.karlrunge.com/x11vnc/faq.html#faq-display-manager"))
otherwise all xapps (x11vnc included) are killed right after you log in via GDM.  Maybe you have done this already.

This /etc/gdm/Init/Default method is really quite simple (except for the KillInitClients gotcha, but that is only for the GDM case). You just add one line to one file.

I suggest you **undo everything else** you may have done (e.g. no PreSession, no sudo, no init.d, no inetd, etc.)

---

### Post by Darth_tater on 2008-07-13
you right.  my mistake.  i didn't fully understand what the FAQ was saying.

As soon as i get my connection restored, i will SSH and double check to make sure that i have reversed everything.

-- thanks for all your help so far.

edit:  yes, i have modified  the gdm.conf file to reflect this change:  KillInitClients=false

---

### Post by krunge on 2008-07-13
> **Darth_tater said:**
> you right.  my mistake.  i didn't fully understand what the FAQ was saying.

As soon as i get my connection restored, i will SSH and double check to make sure that i have reversed everything.


That sounds good.  Let us know how it goes.

BTW, I see in your config you use the x11vnc "-usepw" option.  You better make sure the password file has already been created (I'm guessing since gdm runs as root the file will be /root/.vnc/passwd), otherwise your x11vnc will block prompting for the user to set an initial VNC passwd.

I think it is safer to create the password file manually, e.g.
```
x11vnc -storepasswd /etc/x11vnc-pw
```
(x11vnc will prompt for the password. The above would need to be done as root/sudo to write to /etc, otherwise use a different path).

And then explicitly point to the file in your x11vnc line in gdm Default script:
```

/usr/bin/x11vnc -rfbauth /etc/x11vnc-pw -o /var/log/x11vnc.log -bg -rfbport 5900 -forever

```
Then I think the above line in /etc/gdm/Init/Default will be all you need.

---

### Post by Darth_tater on 2008-07-13
> **krunge said:**
> That sounds good.  Let us know how it goes.

BTW, I see in your config you use the x11vnc "-usepw" option.  You better make sure the password file has already been created (I'm guessing since gdm runs as root the file will be /root/.vnc/passwd), otherwise your x11vnc will block prompting for the user to set an initial VNC passwd.

I think it is safer to create the password file manually, e.g.
```
x11vnc -storepasswd /etc/x11vnc-pw
```
(x11vnc will prompt for the password. The above would need to be done as root/sudo to write to /etc, otherwise use a different path).

And then explicitly point to the file in your x11vnc line in gdm Default:
```

/usr/bin/x11vnc -rfbauth /etc/x11vnc-pw -o /var/log/x11vnc.log -bg -rfbport 5900 -forever

```
Then I think the above line in gdm Default will be all you need.


you know what... i think it was the -usepw line.

the first time i ran that, i was logged in as my user account.  not root.

that might have been screwing me up.

i don't yet have my connection restored, so ill let you know what happens when i get it up and running :)

---

### Post by Darth_tater on 2009-08-16
Sorry to digg up this old thread, but im having the same issue w/ ubuntu 9.4

i followed *all* the steps i had done before and this is the problem i get

---- ubuntu 9.4 -----

1) add the folowing to /etc/gdm/Init/Default file
```
/usr/bin/x11vnc -rfbauth /etc/x11vnc-pw -o /var/log/x11vnc.log -bg -rfbport 5900 -forever -allow "127.0.0.1","192.168.2."
```

2) go to /etc/gdm/gdm.conf and uncomment then change the line to read like this
```
KillInitClients=false
```

3) restart and test.

------

Here are the results:

everything starts up properly, and i can verify this because i can connect via VNC and see a remote copy of my physical screen.

Logging in poses a problem.  The only way i can log in is via the physical keyboard WITH NO ACTIVE VNC SESSION.  If i try logging in w/ a connected VNC client, then GDM seems to restart and asks me again for my user/pass.

If i try logging in through VNC, then the same thing happens, except during the brief gdm restart, my VNC client throws a connection closed error.


once i login (through physical keyboard only), everything runs fine!  i can remote connect and go w/o any problems.

it seems that there is some step that the FAQ doesn't include or needs to include for newer versions of GDM.

---

### Post by krunge on 2009-08-16
> **Darth_tater said:**
> Logging in poses a problem.  The only way i can log in is via the physical keyboard WITH NO ACTIVE VNC SESSION.  If i try logging in w/ a connected VNC client, then GDM seems to restart and asks me again for my user/pass.

If i try logging in through VNC, then the same thing happens, except during the brief gdm restart, my VNC client throws a connection closed error.

once i login (through physical keyboard only), everything runs fine!  i can remote connect and go w/o any problems.

I think you are seeing this problem:
[INDENT][http://ubuntuforums.org/showthread.php?t=965695&highlight=x11vnc+noxfixes+reopen&page=2](http://ubuntuforums.org/showthread.php?t=965695&highlight=x11vnc+noxfixes+reopen&page=2)
[/INDENT]
Let me know if you agree or not.  The workaround is:```
x11vnc -noxfixes ...
```As discussed in that thread there is also an option "-reopen" in the upstream x11vnc that provides another workaround.

---

### Post by Darth_tater on 2009-08-16
> **krunge said:**
> I think you are seeing this problem:
[INDENT][http://ubuntuforums.org/showthread.php?t=965695&highlight=x11vnc+noxfixes+reopen&page=2](http://ubuntuforums.org/showthread.php?t=965695&highlight=x11vnc+noxfixes+reopen&page=2)
[/INDENT]
Let me know if you agree or not.  The workaround is:```
x11vnc -noxfixes ...
```As discussed in that thread there is also an option "-reopen" in the upstream x11vnc that provides another workaround.

yes!  that works miracles!  im glad i wasn't the first one to find this bug... this functionality is pretty important to me.

for those who dont want to go digging through the other thread, this is all you need to use

```
/usr/bin/x11vnc -rfbauth /etc/x11vnc-pw -o /var/log/x11vnc.log -bg -rfbport 5900 -forever -allow "127.0.0.1","192.168.2." -noxfixes -cursor arrow -arrow 3 
```

---

### Post by krunge on 2009-08-16
> **Darth_tater said:**
> yes!  that works miracles!  im glad i wasn't the first one to find this bug... this functionality is pretty important to me.

Great, glad it is working for you.

Feel free to add a "Me too" to any of the bug reports mentioned in the other thread.  Xorg seems to be ignoring this bug...

---

### Post by Darth_tater on 2009-08-17
> **krunge said:**
> Great, glad it is working for you.

Feel free to add a "Me too" to any of the bug reports mentioned in the other thread.  Xorg seems to be ignoring this bug...


in the hopes that the bug is fixed, i have posted a "me to" to the bugreport i was able to find

[http://bugs.freedesktop.org/show_bug.cgi?id=18451](http://bugs.freedesktop.org/show_bug.cgi?id=18451)

cheers!  and thanks for the help!

---

