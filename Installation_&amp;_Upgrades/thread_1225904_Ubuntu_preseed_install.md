---
title: "Ubuntu preseed install"
date: 2009-07-29
forum: Installation &amp; Upgrades
---

### Post by Frye on 2009-07-29
Hi,

I am trying to get a preseed install to work, and actually it works just fine until I need to interact with the user during the late script. And this is where I am out of luck. How can I ask a question from the user and get the input when preseeding? If it is easier to interact with the user during the script in the beginning of installation that is also ok. Curently I have tried debconf interface, but it does not bring any questions to the installer interface. I believe this is because I was running it from the chrooted target, and it did not have the connection to the frontend. I'll try to look into this today to see if I can get a basic shell script to work outside the chrooted environment.

Idea is that the actuall installation is totally automated (Software package selection, disk layout and apt config etc... standardized), but few configuration settings would be asked from the user, so that I would not need to create a separate preseed file / user.

Thanks in advance,

---

### Post by Frye on 2009-07-30
To reply to myself.

If you need to get a custom dialog displayed during early / late commands this is a quick example how I managed to do it. Of course there are many more options for templates than just text, but as I said this is a REALLY simple example.

```
#! /bin/sh
# Example early script to show custom dialog

# Source debconf library
. /usr/share/debconf/confmodule

# Create debconf template on-the-fly
cat > /tmp/example.template <<'!EOF!'
Template: example-config/text
Type: text
Description: Hello World!
 Simple template for displaying some basic text.

Template: example-config/title
Type: text
Description: Example Title
!EOF!

# Load the template that was just created
debconf-loadtemplate example-config /tmp/example.template

# Set title for the dialog
db_settitle example-config/title

# Set the dialog importance to critical. Not necessarily wise, but in this
# example we want it to be displayed even when preseeding the installation.
db_input critical example-config/text

# This statement is actually when the dialog gets displayed.
db_go

# If the field was requesting user input instead of just being informative
# this is how you get the value back in the script
# db_get example-config/text
# echo "$RET" > /tmp/example.value
# So the user input resides in the variable $RET in this case however there
# is nothing in that variable as the dialog was only to display basic text.
# Or you could switch to VC 2 for example and check the value with
# debconf-get example-config/text
# Other pretty useful types are: string, boolean and error to name a few.

```

---

### Post by relay23 on 2009-09-04
This is really nice, thanks, I'm having a devil of a time getting the normal ubiquity-based installed installer to apply my preseed file.. i can tell it's reading it from the logs but it is not setting my options.. did you have to use the Alternate CD?? 

Thanks

---

