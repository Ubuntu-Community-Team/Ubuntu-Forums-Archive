---
title: "session lasted longer than 10 seconds....cannot get past log in /etc/gdm/Xsession"
date: 2008-10-02
forum: General Help
---

### Post by DozerLink on 2008-10-02
using ubuntu 8.04
hey all, today all of a sudden I couldnt get past the log in screen, the last thing I seem to remember doing was one of the updates to the OS.  Anyway, here is the error I get:

/etc/gdm/Xsession: Beginning session setup...
export: 30: DR.: bad variable name


anyone know how I can restore the Xsession file to what it should be or what else I might need to do?  Ill also post my Xsession file here jic it helps.  Not sure if it will or not but hey who knows?  Not me:

#!/bin/sh
#
# This is SORT OF LIKE an X session, but not quite.  You get a command as the
# first argument (it could be multiple words, so run it with "eval").  As a
# special case, the command can be:
#  failsafe - Run an xterm only
#  default - Run the appropriate Xclients startup (see the code below)
#  custom - Run ~/.xsession and if that's not available run 'default'
#
# (Note that other arguments could also follow, but only the command one is
# right now relevant and supported)
#
# The output is ALREADY redirected to .xsession-errors in GDM.  This way
# .xsession-errors actually gets more output such as if the PreSession script
# is failing.  This also prevents DoS attacks if some app in the users session
# can be prodded to dump lots of stuff on the stdout/stderr.  We wish to be
# robust don't we?  In case you wish to use an existing script for other DM's,
# you can just not redirect when GDMSESSION is set.  GDMSESSION will always
# be set from gdm.
#
# Also note that this is not run as a login shell, this is just executed.
#
# based on:
# $XConsortium: Xsession /main/10 1995/12/18 18:21:28 gildea $

PROGNAME=Xsession

message () {
  # pretty-print messages of arbitrary length; use xmessage if it
  # is available and $DISPLAY is set
  MESSAGE="$PROGNAME: $*"
  echo "$MESSAGE" | fold -s -w ${COLUMNS:-80} >&2
  if [ -n "$DISPLAY" ]; then
    if [ -n "$zenity" ]; then
      "$zenity" --info --text "`gettextfunc "$MESSAGE"`"
    elif [ -n "$xmessage" ]; then
      echo "$MESSAGE" | fold -s -w ${COLUMNS:-80} | $xmessage -center -file -
    fi
  fi
}

message_nonl () {
  # pretty-print messages of arbitrary length (no trailing newline); use
  # xmessage if it is available and $DISPLAY is set
  MESSAGE="$PROGNAME: $*"
  echo -n "$MESSAGE" | fold -s -w ${COLUMNS:-80} >&2;
  if [ -n "$DISPLAY" ]; then
    if [ -n "$zenity" ]; then
      "$zenity" --info --text "`gettextfunc "$MESSAGE"`"
    elif [ -n "$xmessage" ]; then
      "$zenity" --info --text "`gettextfunc "$MESSAGE"`"
    elif [ -n "$xmessage" ]; then
      echo -n "$MESSAGE" | fold -s -w ${COLUMNS:-80} | $xmessage -center -file -
    fi
  fi
}

errormsg () {
  # exit script with error
  message "$*"
  exit 1
}

internal_errormsg () {
  # exit script with error; essentially a "THIS SHOULD NEVER HAPPEN" message
  # One big call to message() for the sake of xmessage; if we had two then
  # the user would have dismissed the error we want reported before seeing the
  # request to report it.
  errormsg "$*" \
           "Please report the installed version of the \"xfree86-common\"" \
           "package and the complete text of this error message to" \
           "<debian-x@lists.debian.org>."
}

run_parts () {
  # until run-parts --noexec is implemented
  if [ -z "$1" ]; then
    internal_errormsg "run_parts() called without an argument."
  fi
  if [ ! -d "$1" ]; then
    internal_errormsg "run_parts() called, but \"$1\" does not exist or is" \
                      "not a directory."
  fi
  for F in $(ls $1); do
    if expr "$F" : '[[:alnum:]_-]\+$' > /dev/null 2>&1; then
      if [ -f "$1/$F" ]; then
        echo "$1/$F"
      fi
    fi
  done
}
# initialize variables for use by all session scripts

OPTIONFILE=/etc/X11/Xsession.options

SYSRESOURCES=/etc/X11/Xresources
USRRESOURCES=$HOME/.Xresources

SYSSESSIONDIR=/etc/X11/Xsession.d
USERXSESSION=$HOME/.xsession
SYSSESSIONDIR=/etc/X11/Xsession.d
USERXSESSION=$HOME/.xsession
USERXSESSIONRC=$HOME/.xsessionrc
ALTUSERXSESSION=$HOME/.Xsession

# this will go into the .xsession-errors along with all other echo's
# good for debugging where things went wrong
echo "$0: Beginning session setup..."

# First read /etc/profile and .profile
test -f /etc/profile && . /etc/profile
test -f "$HOME/.profile" && . "$HOME/.profile"
# Second read /etc/xprofile and .xprofile for X specific setup
test -f /etc/xprofile && . /etc/xprofile
test -f "$HOME/.xprofile" && . "$HOME/.xprofile"

# Translation stuff
if [ -x "/usr/lib/gdm/gdmtranslate" ] ; then
  gdmtranslate="/usr/lib/gdm/gdmtranslate"
else
  gdmtranslate=
fi

# Note that this should only go to zenity dialogs which always expect utf8
gettextfunc () {
  if [ "x$gdmtranslate" != "x" ] ; then
    "$gdmtranslate" --utf8 "$1"
  else
    echo "$1"
  fi
}

zenity=`which zenity 2>/dev/null`
xmessage=`which xmessage 2>/dev/null`

command="$1"

if [ -z "$command" ] ; then
  command=failsafe
fi

if [ x"$command" = xfailsafe ] ; then
  if [ -n "$zenity" ] ; then
    "$zenity" --info --text "`gettextfunc "This is the failsafe xterm session.  Windows now have focus only if you have your cursor above them.  To get out of this mode type 'exit' in the window in the upp$
  else
    echo "$0: Starting the failsafe xterm session."
  fi
  exec xterm -geometry 80x24+0+0
fi
fi

# clean up after xbanner
freetemp=`which freetemp 2>/dev/null`
if [ -n "$freetemp" ] ; then
        "$freetemp"
fi

usermodmap="$HOME/.Xmodmap"
userxkbmap="$HOME/.Xkbmap"

if [ -f "$userxkbmap" ]; then
    setxkbmap `cat "$userxkbmap"`
    XKB_IN_USE=yes
fi

# xkb and xmodmap don't play nice together
if [ -z "$XKB_IN_USE" ]; then
    if [ -f "$usermodmap" ]; then
       xmodmap "$usermodmap"
    fi
fi

unset XKB_IN_USE

# if GDM_LANG isn't first in LANGUAGE, then unset it.
if [ -n "$GDM_LANG" ]; then
    if [ -n "$LANGUAGE" ]; then
        if echo "$LANGUAGE" | grep -q -- "^$GDM_LANG"; then
           :
        else
           unset LANGUAGE
        fi
    fi
fi

# The default Debian session runs xsession first, so we just do that for
# "custom"
if [ "x$command" = "xcustom" ] ; then
  shift
  set default $*
fi

# use run-parts to source every file in the session directory; we source
# instead of executing so that the variables and functions defined above
# are available to the scripts, and so that they can pass variables to each
# other
SESSIONFILES=$(run_parts $SYSSESSIONDIR)
if [ -n "$SESSIONFILES" ]; then
  for SESSIONFILE in $SESSIONFILES; do
if [ -n "$SESSIONFILES" ]; then
  for SESSIONFILE in $SESSIONFILES; do
    . $SESSIONFILE
  done
fi

echo "$0: Executing $command failed, will try to run x-terminal-emulator"

if [ -n "$zenity" ] ; then
        "$zenity" --info --text "`gettextfunc "I could not start your session and so I have started the failsafe xterm session.  Windows now have focus only if you have your cursor above them.  To get out $
fi

exec x-terminal-emulator -geometry 80x24+0+0

---

### Post by DozerLink on 2008-10-03
a bit more info - I can boot to the gnome failsafe session just fine so the problem seems to be with some of my startup scripts maybe?

EDIT: after looking closer at that log in error I am noticing it is saying "DR." is a bad variable name.  I am using this for a class and inserted this in /etc/profile:

INSTRUCTOR="DR. GIDDENS"
export INSTRUCTOR

I commented that out but I am currently in class so don't have a chance to test it yet...I'll post my results soon

---

### Post by DozerLink on 2008-10-03
yep, that fixed it, feel free to remove this thread

---

### Post by Mikorist on 2008-10-03
> **DozerLink said:**
> 

INSTRUCTOR="DR. GIDDENS"
export INSTRUCTOR



You realized what was happened right here or [there]("http://www.cybertechhelp.com/forums/showthread.php?p=1040968")
DR. GIDDENS ?

---

### Post by DozerLink on 2008-10-03
miko - yes I posted this on two different websites hoping to get an answer from one of them, so what is your point?

---

### Post by Mikorist on 2008-10-04
> **DozerLink said:**
> miko - yes I posted this on two different websites hoping to get an answer from one of them, so what is your point?


Just wondering what is going on here in your point of view. 
Sorry...I don't think nothing bad...

:(

---

### Post by yus253 on 2009-10-16
> **DozerLink said:**
> using ubuntu 8.04
hey all, today all of a sudden I couldnt get past the log in screen, the last thing I seem to remember doing was one of the updates to the OS.  Anyway, here is the error I get:

/etc/gdm/Xsession: Beginning session setup...
export: 30: DR.: bad variable name


anyone know how I can restore the Xsession file to what it should be or what else I might need to do?  Ill also post my Xsession file here jic it helps.  Not sure if it will or not but hey who knows?  Not me:

#!/bin/sh
#
# This is SORT OF LIKE an X session, but not quite.  You get a command as the
# first argument (it could be multiple words, so run it with "eval").  As a
# special case, the command can be:
#  failsafe - Run an xterm only
#  default - Run the appropriate Xclients startup (see the code below)
#  custom - Run ~/.xsession and if that's not available run 'default'
#
# (Note that other arguments could also follow, but only the command one is
# right now relevant and supported)
#
# The output is ALREADY redirected to .xsession-errors in GDM.  This way
# .xsession-errors actually gets more output such as if the PreSession script
# is failing.  This also prevents DoS attacks if some app in the users session
# can be prodded to dump lots of stuff on the stdout/stderr.  We wish to be
# robust don't we?  In case you wish to use an existing script for other DM's,
# you can just not redirect when GDMSESSION is set.  GDMSESSION will always
# be set from gdm.
#
# Also note that this is not run as a login shell, this is just executed.
#
# based on:
# $XConsortium: Xsession /main/10 1995/12/18 18:21:28 gildea $

PROGNAME=Xsession

message () {
  # pretty-print messages of arbitrary length; use xmessage if it
  # is available and $DISPLAY is set
  MESSAGE="$PROGNAME: $*"
  echo "$MESSAGE" | fold -s -w ${COLUMNS:-80} >&2
  if [ -n "$DISPLAY" ]; then
    if [ -n "$zenity" ]; then
      "$zenity" --info --text "`gettextfunc "$MESSAGE"`"
    elif [ -n "$xmessage" ]; then
      echo "$MESSAGE" | fold -s -w ${COLUMNS:-80} | $xmessage -center -file -
    fi
  fi
}

message_nonl () {
  # pretty-print messages of arbitrary length (no trailing newline); use
  # xmessage if it is available and $DISPLAY is set
  MESSAGE="$PROGNAME: $*"
  echo -n "$MESSAGE" | fold -s -w ${COLUMNS:-80} >&2;
  if [ -n "$DISPLAY" ]; then
    if [ -n "$zenity" ]; then
      "$zenity" --info --text "`gettextfunc "$MESSAGE"`"
    elif [ -n "$xmessage" ]; then
      "$zenity" --info --text "`gettextfunc "$MESSAGE"`"
    elif [ -n "$xmessage" ]; then
      echo -n "$MESSAGE" | fold -s -w ${COLUMNS:-80} | $xmessage -center -file -
    fi
  fi
}

errormsg () {
  # exit script with error
  message "$*"
  exit 1
}

internal_errormsg () {
  # exit script with error; essentially a "THIS SHOULD NEVER HAPPEN" message
  # One big call to message() for the sake of xmessage; if we had two then
  # the user would have dismissed the error we want reported before seeing the
  # request to report it.
  errormsg "$*" \
           "Please report the installed version of the \"xfree86-common\"" \
           "package and the complete text of this error message to" \
           "<debian-x@lists.debian.org>."
}

run_parts () {
  # until run-parts --noexec is implemented
  if [ -z "$1" ]; then
    internal_errormsg "run_parts() called without an argument."
  fi
  if [ ! -d "$1" ]; then
    internal_errormsg "run_parts() called, but \"$1\" does not exist or is" \
                      "not a directory."
  fi
  for F in $(ls $1); do
    if expr "$F" : '[[:alnum:]_-]\+$' > /dev/null 2>&1; then
      if [ -f "$1/$F" ]; then
        echo "$1/$F"
      fi
    fi
  done
}
# initialize variables for use by all session scripts

OPTIONFILE=/etc/X11/Xsession.options

SYSRESOURCES=/etc/X11/Xresources
USRRESOURCES=$HOME/.Xresources

SYSSESSIONDIR=/etc/X11/Xsession.d
USERXSESSION=$HOME/.xsession
SYSSESSIONDIR=/etc/X11/Xsession.d
USERXSESSION=$HOME/.xsession
USERXSESSIONRC=$HOME/.xsessionrc
ALTUSERXSESSION=$HOME/.Xsession

# this will go into the .xsession-errors along with all other echo's
# good for debugging where things went wrong
echo "$0: Beginning session setup..."

# First read /etc/profile and .profile
test -f /etc/profile && . /etc/profile
test -f "$HOME/.profile" && . "$HOME/.profile"
# Second read /etc/xprofile and .xprofile for X specific setup
test -f /etc/xprofile && . /etc/xprofile
test -f "$HOME/.xprofile" && . "$HOME/.xprofile"

# Translation stuff
if [ -x "/usr/lib/gdm/gdmtranslate" ] ; then
  gdmtranslate="/usr/lib/gdm/gdmtranslate"
else
  gdmtranslate=
fi

# Note that this should only go to zenity dialogs which always expect utf8
gettextfunc () {
  if [ "x$gdmtranslate" != "x" ] ; then
    "$gdmtranslate" --utf8 "$1"
  else
    echo "$1"
  fi
}

zenity=`which zenity 2>/dev/null`
xmessage=`which xmessage 2>/dev/null`

command="$1"

if [ -z "$command" ] ; then
  command=failsafe
fi

if [ x"$command" = xfailsafe ] ; then
  if [ -n "$zenity" ] ; then
    "$zenity" --info --text "`gettextfunc "This is the failsafe xterm session.  Windows now have focus only if you have your cursor above them.  To get out of this mode type 'exit' in the window in the upp$
  else
    echo "$0: Starting the failsafe xterm session."
  fi
  exec xterm -geometry 80x24+0+0
fi
fi

# clean up after xbanner
freetemp=`which freetemp 2>/dev/null`
if [ -n "$freetemp" ] ; then
        "$freetemp"
fi

usermodmap="$HOME/.Xmodmap"
userxkbmap="$HOME/.Xkbmap"

if [ -f "$userxkbmap" ]; then
    setxkbmap `cat "$userxkbmap"`
    XKB_IN_USE=yes
fi

# xkb and xmodmap don't play nice together
if [ -z "$XKB_IN_USE" ]; then
    if [ -f "$usermodmap" ]; then
       xmodmap "$usermodmap"
    fi
fi

unset XKB_IN_USE

# if GDM_LANG isn't first in LANGUAGE, then unset it.
if [ -n "$GDM_LANG" ]; then
    if [ -n "$LANGUAGE" ]; then
        if echo "$LANGUAGE" | grep -q -- "^$GDM_LANG"; then
           :
        else
           unset LANGUAGE
        fi
    fi
fi

# The default Debian session runs xsession first, so we just do that for
# "custom"
if [ "x$command" = "xcustom" ] ; then
  shift
  set default $*
fi

# use run-parts to source every file in the session directory; we source
# instead of executing so that the variables and functions defined above
# are available to the scripts, and so that they can pass variables to each
# other
SESSIONFILES=$(run_parts $SYSSESSIONDIR)
if [ -n "$SESSIONFILES" ]; then
  for SESSIONFILE in $SESSIONFILES; do
if [ -n "$SESSIONFILES" ]; then
  for SESSIONFILE in $SESSIONFILES; do
    . $SESSIONFILE
  done
fi

echo "$0: Executing $command failed, will try to run x-terminal-emulator"

if [ -n "$zenity" ] ; then
        "$zenity" --info --text "`gettextfunc "I could not start your session and so I have started the failsafe xterm session.  Windows now have focus only if you have your cursor above them.  To get out $
fi

exec x-terminal-emulator -geometry 80x24+0+0

hey,doz .I think I must have been  meeting the same problem with you .Could you tell me how to you do at the  end .

---

