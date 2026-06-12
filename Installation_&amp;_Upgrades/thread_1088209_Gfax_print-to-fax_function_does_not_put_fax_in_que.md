---
title: "Gfax print-to-fax function does not put fax in queue"
date: 2009-03-05
forum: Installation &amp; Upgrades
---

### Post by Ralph L on 2009-03-05
Am running a Dell Latitude D610 laptop with an integral "winmodem" under ubuntu intrepid.  I am trying to use the print-to-fax function of gfax.  By following the instruction in [http://penguin.cc.mala.bc.ca/pipermail/gfax/2008-February/000612.html](http://penguin.cc.mala.bc.ca/pipermail/gfax/2008-February/000612.html) and creating the two files listed below then reinstalling gfax (using Synaptic), a fax printer was automatically installed (it appears as a selection in all File>Print selections).  However, when I print to the fax, it appears that everything is fine except no fax is ever sent.  When I checked the fax spool file at ~/.local/share/gfax/spool, I see that no entry is made.

However, if I launch gfax from the main menu, click the New Fax button, enter a .ps file and a phone number, the fax file appears in the spool folder and the modem is dialed (I can hear it dialing).  I am using efax-gtk as the fax dialer and sender.  So efax is obviously looking in the gfax spool folder and picking up fax files to send.  The problem is that the print-to-fax function of gfax is not putting fax files in the spool folder.

I have not been able to determine if print-to-fax is actually creating the fax file and not putting into the spool, or if it is not creating the file at all.  It could have something to do with permissions, but I am the user doing the print-to-fax and the spool folder is in my home folder, so it seems like there should be no problem.

One approach to solving the problem might be to look at the appropriate log file to see if print-to-fax put out any error messages.  However, I am too much of a newbie to know how to do that.  Any hints on how to find logs would be appreciated.

I would very much appreciate any help (or any hints).  Apparently few people run gfax so it is hard to find anything on the web.

Thank you very much,
Ralph

For the partial solution to this problem please see [http://ubuntuforums.org/showthread.php?p=6832477#post6832477](http://ubuntuforums.org/showthread.php?p=6832477#post6832477)


Edit //usr/lib/cups/backend/gfax
----------
/

#!/bin/bash

# Script di Backend per Gnome-Print 2.2

FAXPRG=/usr/bin/gfaxcups
if [ $# -eq 0 ]; then
        if [ ! -x "$FAXPRG" ]; then
                echo "ERROR: Can't find program $FAXPRG" 1>&2
                exit 0
        fi
        echo "direct gfax:/local \"Unknown\" \"gfax X-application\""
        exit 0
fi

# Get the user that owns the job
USER=$2
sudo -H -u $USER $FAXPRG

/----------/
/
/Edit //usr/bin/gfaxcups/
/----------
/

#!/bin/bash
#  Copyright (c) 2003 George A. Farris 
#
#  NO WARRANTY:
#  
#  THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, 
#  EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES
#  OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NON-
#  INFRINGEMENT.  IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR ANY 
#  CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF 
#  CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECT-
#  ION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
#
RNAME=G$$
# don't change this spool directory, gfax uses it.
SPOOL_DIR=~/.local/share/gfax/spool

# Determino su quale DISPLAY sta girando l'X Server
XGLDIPLAY=`ps -ef |grep "Xgl :" |grep -v grep |awk '{print $9}'`
if [ -z $XGLDIPLAY ]
        then
        export DISPLAY=`ps -ef |grep "/usr/bin/X" |grep -v grep |awk '{print $9}'|uniq`
        else
        export DISPLAY=$XGLDIPLAY
fi

cat > $SPOOL_DIR/D.$RNAME
exec mono /usr/lib/gfax/gfax.exe -f $SPOOL_DIR/D.$RNAME &

/----------
/
After editing those two files, now you can create a new GFax printer
from the "system-config-printer".
The only problem I had was to understand on which $DISPLAY show the GFax
Popup window. I'm sure there are better ways...sorry. :-)


Thanx
Il Davo

---

