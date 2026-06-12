---
title: "using a serial mouse in 9.10 desktop"
date: 2009-11-19
forum: Hardware
---

### Post by raygj on 2009-11-19
to get your old microsoft serial mouse working on COM1 with 9.10 you need to install the gpm package.so in a terminal enter
> sudo apt-get install gpm
then ,after it is installed, you enter in terminal
 
> sudo inputattach --microsoft /dev/ttyS0
now move your mouse around to see that  your serial mouse is working ok.
OK?
now you need to set you computer to run it on startup.
so in a terminal enter 
> sudo gedit /etc/rc.local
an editer window opens with
> 
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0
now enter 


> inputattach --microsoft /dev/ttyS0 

so that the /etc/rc.local file contains
> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

## added serial mouse input ##
inputattach --microsoft /dev/ttyS0

exit 0
now save this file and close editer.
now ,when you re-boot,  your serial mouse will work.

---

