---
title: "Brother MFC 465-CN install questions"
date: 2015-09-09
forum: Hardware
---

### Post by Boyntonstu on 2015-09-09
From the brother website:


 
[LIST]
[*]Download LPR driver.
[*]Login as a superuser ( or use "sudo" option if required).
[*]Check if pre-required procedures are completed
    [**For Debian/Ubuntu 64bit**]("http://support.brother.com/g/s/id/linux/en/before.html#004")
[*]Install the driver.
[LIST]
[*]Turn on the printer and connect the usb, network or parallel cable.
[*]Go to the directory where the driver is.
[*]Install LPR driver.The install process may take some time. Please wait until it is complete. [B]
        Command  :  dpkg -i --force-all  (lpr-drivername)[/B]
[*]Check if the LPR driver is installed.[B]
        Command  :  dpkg -l  |  grep  Brother[/B]
[/LIST]

[*]Confirm/Configure a file according to your connection.
[LIST]
[*]Check the configuration filename for your distribution.
        [B]Example:
        openSUSE, Ubuntu, Debian : /etc/printcap
        Redhat, fedora, Mandriva : /etc/printcap.local [/B]
[*]Edit the file according to your connection.
        _**For USB Connection (Default)**_
        Check if the parameter of ":lp" is ":lp=/dev/usb/lp0"
        _**For Network Connection**_
        replace ":lp" line to the following 2 lines
        :rm=(ip address of your printer)\
        :rp=lp\
        _**For Parallel Connection**_
        replace ":lp" line to the following line
        :lp=/dev/lp0\
[*]Restart the print system. [B]
        Command  (for  lpr):  /etc/init.d/lpr  restart
        Command  (for  lprng)  :  /etc/init.d/lprng  restart [/B]
[/LIST]

[*]Try a test print.
[/LIST]
=========================

I downloaded this file as well:  linux-brprinter-installer-2.0.0-1

It is a script, some of which is this:

ENABLE_FAX_INSTALL=No           # change to Yes if FAX is required 

DEBUG_MSG=0
MSG=1


COLOR='\033[1;31m'
COLOR2='\033[1;35m'
COLOR3='\033[1;32m'
COLOR4='\033[1;34m'
MONO='\033[1;0m'

if [ "$(echo $0 | grep  linux-brjprinter-installer)" = '' ];then
  MESSAGE010="USAGE:  "
  MESSAGE012="     :  "
  MESSAGE020="  model"
  MESSAGE030="   -f model"
  MESSAGE040="   -l "
  MESSAGE050="Only root can perform this operation."
  MESSAGE060="CUPS is not installed."
  MESSAGE070="Do you want to specify a PROXY server? [y/N] ->"
  MESSAGE080="Enter the URL of the PROXY server."
  MESSAGE090="   ex http://(proxy-server-url):(port)"
  MESSAGE100="   ex http://(login-name):(password)@(proxy-server-url):(port)"
  MESSAGE110="     ->"
  MESSAGE120="Unable to get the server information."\
"  Please check the network settings."
  MESSAGE121="Input model name ->"
  MESSAGE122="Rpm or dpkg is required."
  MESSAGE130="Driver-packages cannot be found."
  MESSAGE140=" Confirm the model name."
  MESSAGE150="You are going to install  following packages."
  MESSAGE160="OK? [y/N]  ->"
  MESSAGE165="OK? [Y/n]  ->"
  MESSAGE170="Do you agree? [Y/n] ->"
  MESSAGE180="Do you agree? [Y/n] ->"

----------------------------------------

I am lost.

The script seems to have the solution.

How do I run the script?

  

So far, I am enjoying Lubuntu because it is so clean and fast.   If I can install the printer  and connect to my wife's PC in a Windows Homegroup, I would be 100% satisfied.

---

### Post by dino99 on 2015-09-09
Most of the required drivers are already found into the ubuntu archive.
Mainly "brother-lpr-drivers-extra" should be fine with that model, and automatically proposed for activation via "additional drivers"

---

### Post by Boyntonstu on 2015-09-09
> **dino99 said:**
> Most of the required drivers are already found into the ubuntu archive.
Mainly "brother-lpr-drivers-extra" should be fine with that model, and automatically proposed for activation via "additional drivers"

OK I found this in Vivid:

/usr/Brother/Printer/mfc465cn/inf/brPrintListij2

Next step?

---

### Post by Boyntonstu on 2015-09-10
Problem Solved.  Printer installed!!!

---

