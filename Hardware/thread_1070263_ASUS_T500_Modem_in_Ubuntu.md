---
title: "ASUS T500 Modem in Ubuntu"
date: 2009-02-14
forum: Hardware
---

### Post by ahshimul on 2009-02-14
Hi All,
Hope u r all doing fine.
I  registered to this community just now.

Anyway, I'm facing problems with my Modem ASUS T500.In the installation CD provided with Modem, no Linux installation is there.I tried to find out the Linux installation software on the web but failed.

Is there anyone who is using that in Ubuntu or who can help me how to install in in Ubuntu?

Your help will take one  user from Windows to Ubuntu.:)

Thanks//Ahsan Habib

---

### Post by liju.. on 2009-05-13
Actually I got T500 yesterday and was looking for a way to use it in mu Kubuntu. I saw Your topic and as I found a way to make T500 work on my machine, I share it with You.

Basically You can refer to [http://allabouteeepc.com/how-to-install-t500-on-asus-eee-pc/](http://allabouteeepc.com/how-to-install-t500-on-asus-eee-pc/)

But it will not be all to just have a connection running. T500 was bundled with Asus eeePC which is also shiped with Xandros Linux SKU. This is why there is .deb package which can be used by us as well.

I downloaded driver and utility from support.asus.com at:
[http://dlcdnet.asus.com/pub/ASUS/HSDPA_Cards/T500/T500_Utility_forEeePC_TC_20080222.zip](http://dlcdnet.asus.com/pub/ASUS/HSDPA_Cards/T500/T500_Utility_forEeePC_TC_20080222.zip)

Then I just used noob'y way of double click on the file to install it. After it is installed, no new icon appears in the menu, but inside .deb file You should see /sbin/3gmpt-launch

I was happy I noticed this so I started konsole and typed:
```
sudo 3gmpt-launch
```

but this seemed to be not enough. No window opened, no message was given.

So I cated this:
```
cat /sbin/3gmpt-launch
#!/usr/bin/perl
#
# Xandros Corporation Copyright 2006.
#
use POSIX;

$User="";
$PrimaryDisplay=":0.0";
$Su="/bin/su";
$Who="/usr/bin/w";
$Grep="/bin/grep";
$Cut="/usr/bin/cut";

if( $ENV{"ACTION"} eq "add" )
{
        system("rm -f /tmp/log");
        $ENV{'XAUTHORITY'} = "/home/user/.Xauthority";
        system("export DISPLAY=\":0.0\";test -f /home/user/.bash_profile && source /home/user/.bash_profile;/bin/su user  -c \"/usr/bin/xhost +local: \" > /dev/null 2>&1");
        system("export DISPLAY=\":0\"; test -f /home/user/.bash_profile && source /home/user/.bash_profile ; nice --adjustment=5 $Su user -c \"/opt/3gmpt/run-3g.sh&\" > /dev/null 2>&1 \\&");
}
exit 0;

```

Well well, seems there is in fact other app that starts what we need...

I went to /opt/3gmpt/ and saw there is "ui" file indeed. I like graphical user interfaces, so I started it with sudo command (in order to let it set up my network interface):

```
sudo ui
```

and nice window with "Connect" button appeared. There was also 2nd one asking for a pin which I gave to it and soon was able to surf using T500 :D

Just remember to put down Your current connection before using 3g.

I had no time to prepare one script to do all by auto, but it should not be big problem.

BR,
Liju

---

### Post by ahshimul on 2010-06-05
> **liju.. said:**
> Actually I got T500 yesterday and was looking for a way to use it in mu Kubuntu. I saw Your topic and as I found a way to make T500 work on my machine, I share it with You.

Basically You can refer to [http://allabouteeepc.com/how-to-install-t500-on-asus-eee-pc/](http://allabouteeepc.com/how-to-install-t500-on-asus-eee-pc/)

But it will not be all to just have a connection running. T500 was bundled with Asus eeePC which is also shiped with Xandros Linux SKU. This is why there is .deb package which can be used by us as well.

I downloaded driver and utility from support.asus.com at:
[http://dlcdnet.asus.com/pub/ASUS/HSDPA_Cards/T500/T500_Utility_forEeePC_TC_20080222.zip](http://dlcdnet.asus.com/pub/ASUS/HSDPA_Cards/T500/T500_Utility_forEeePC_TC_20080222.zip)

Then I just used noob'y way of double click on the file to install it. After it is installed, no new icon appears in the menu, but inside .deb file You should see /sbin/3gmpt-launch

I was happy I noticed this so I started konsole and typed:
```
sudo 3gmpt-launch
```

but this seemed to be not enough. No window opened, no message was given.

So I cated this:
```
cat /sbin/3gmpt-launch
#!/usr/bin/perl
#
# Xandros Corporation Copyright 2006.
#
use POSIX;

$User="";
$PrimaryDisplay=":0.0";
$Su="/bin/su";
$Who="/usr/bin/w";
$Grep="/bin/grep";
$Cut="/usr/bin/cut";

if( $ENV{"ACTION"} eq "add" )
{
        system("rm -f /tmp/log");
        $ENV{'XAUTHORITY'} = "/home/user/.Xauthority";
        system("export DISPLAY=\":0.0\";test -f /home/user/.bash_profile && source /home/user/.bash_profile;/bin/su user  -c \"/usr/bin/xhost +local: \" > /dev/null 2>&1");
        system("export DISPLAY=\":0\"; test -f /home/user/.bash_profile && source /home/user/.bash_profile ; nice --adjustment=5 $Su user -c \"/opt/3gmpt/run-3g.sh&\" > /dev/null 2>&1 \\&");
}
exit 0;

```

Well well, seems there is in fact other app that starts what we need...

I went to /opt/3gmpt/ and saw there is "ui" file indeed. I like graphical user interfaces, so I started it with sudo command (in order to let it set up my network interface):

```
sudo ui
```

and nice window with "Connect" button appeared. There was also 2nd one asking for a pin which I gave to it and soon was able to surf using T500 :D

Just remember to put down Your current connection before using 3g.

I had no time to prepare one script to do all by auto, but it should not be big problem.

BR,
Liju
Hi Liju, many thanks although its very late! However, I still need your help.When I open the graphical interface, it show 4 predefined networks of another country. Is there anyway to change that?

I also want to edit wvdial file which is created when the modem was installed.Where I can find wvdial.conf or similar category file.

---

