---
title: "Belkin 550VA Battery Backup install"
date: 2020-12-03
forum: Hardware
---

### Post by ggrillea on 2020-12-03
I was wondering if anybody knows how to install a battery back up package Belkin 550VA: [https://www.belkin.com/us/support-product?pid=01t30000000U38PAAS](https://www.belkin.com/us/support-product?pid=01t30000000U38PAAS)

In the manual after Apple/Microsoft install they have this paragraph:

"[FONT=sans-serif] Other Platforms [/FONT][FONT=sans-serif]&#8226;    This CD provides two installation modes: GUI mode and Console mode. Enter [/FONT][FONT=sans-serif]the directory according the system and run setup.bin or setup_console.[/FONT][FONT=sans-serif]bin to start the installation program. Note: For UnixWare, Irix and Tru64 [/FONT][FONT=sans-serif]platform, make sure JRE1.3.1 has been install in your system, then enter the  [/FONT][FONT=sans-serif]/GenericUnix directory and run setup.bin or setup_console.bin to start the [/FONT][FONT=sans-serif]setup. [/FONT][FONT=sans-serif]&#8226;    Read the information provided, then click Next. [/FONT][FONT=sans-serif]&#8226;    Review the installation options that you have selected. If the options are [/FONT][FONT=sans-serif]correct, then click Install to begin the installation. [/FONT][FONT=sans-serif]&#8226;    When the installation program is completed, click Done"


When I open the CD file I found this very long document:


#!/bin/sh
# Copyright (c) 2001, Belkin Components.
# Script Name: install
# Platform: Linux (RedHat 5.2)
# Date: Dec/06/2001
# Description: Bulldog Plus Installation Program

INSTALL_PATH=""

check_user()
{
    set `/usr/bin/whoami`
    if [ $1 != "root" ]
    then
        echo "You must login under root to execute the program."
        echo "Bye !"
        exit
    fi
}

check_exist()
{
    exist=`/bin/ps x | grep upsd | awk '$5 ~ /\x2fupsd/ { print $1 }'`
    if [ -n "$exist" ]
    then
        echo "The upsd daemon is running, so you must stop it before installation."
        echo "Bye !"
        exit
    fi
}

disp_title()
{
    clear
    echo "+----------------------------------------------+"
    echo "|   Belkin Bulldog Plus Installation Program   |"
    echo "+----------------------------------------------+"
    echo
}

delay()
{
    echo -n "."
}

set_COMPort()
{
    echo
    echo "Please enter the COM port which connects to your UPS."
    echo "For example: COM1 is /dev/ttyS0, COM2 is /dev/ttyS1, USB is /dev/usb."
    echo -n "COM Port: "
    read COMPort
    if [ $COMPort = "/dev/usb" ] 
    then
        echo $COMPort > $INSTALL_PATH/INSTALL.TMP
    elif [ $COMPort ]
    then
        exist=`/bin/ls $COMPort 2> /dev/null | grep $COMPort`
        if [ $exist ]
        then
            echo $COMPort > $INSTALL_PATH/INSTALL.TMP
        else
            echo
            echo $COMPort": Invalid device!"
            echo "Installation failed!"
            exit
        fi
    else
        echo
        echo "Invalid input!"
        echo "Installation failed!"
        exit
    fi
}

set_Master_IP()
{
    echo
    echo "Please enter the IP address of the master "
    echo "which this computer will connect to."
    echo -n "IP address is : "
    read Master_IP
    if [ $Master_IP ]
    then
        echo $Master_IP >> $INSTALL_PATH/PRO_NET.DAT
    else
        echo "Invalid input!"
        echo "Installation failed!"
        exit
    fi
}

set_Master_Slave()
{
    echo
    echo "Please select the communication mode."
    echo "1. Master:"
    echo "   If this computer connects to an UPS directly(RS232 or USB)"
    echo "   and will administrate the UPS."
    echo "2. Serial Slave:"
    echo "   If this computer connects to an UPS directly(RS232 or USB)"
    echo "   but will only monitor the UPS."
    echo "3. Networking Slave:"
    echo "   If this computer powered by an UPS but doesn't communicate"
    echo "   with the UPS directly."
    echo -n "Please enter '1' for Master, '2' for Serial Slave or '3' for Networking Slave: "
    read Master
    if [ $Master ]
    then
        if [ $Master = "1" ]
        then
            rm $INSTALL_PATH/PRO_NET.DAT 2> /dev/null
            echo "1" > $INSTALL_PATH/PRO_NET.DAT
            echo "2710" >> $INSTALL_PATH/PRO_NET.DAT
            echo >> $INSTALL_PATH/PRO_NET.DAT
            set_COMPort
        elif [ $Master = "2" ]
        then
            rm $INSTALL_PATH/PRO_NET.DAT 2> /dev/null
            echo "2" > $INSTALL_PATH/PRO_NET.DAT
            echo "2710" >> $INSTALL_PATH/PRO_NET.DAT
            echo >> $INSTALL_PATH/PRO_NET.DAT
            set_COMPort
        elif [ $Master = "3" ]
        then
            rm $INSTALL_PATH/PRO_NET.DAT 2> /dev/null
            echo "0" > $INSTALL_PATH/PRO_NET.DAT
            echo "2710" >> $INSTALL_PATH/PRO_NET.DAT
            set_Master_IP
        else
            echo "Invalid input!"
            echo "Installation failed!"
            exit
        fi
    else
        echo "Invalid input!"
        echo "Installation failed!"
        exit
    fi
}

start_upsd()
{
    echo -n "Do you want to start upsd now ?[y|n] "
    read start
    if [ $start = "y" ]
    then
        echo
        echo -n "Starting upsd ... "
        $INSTALL_PATH/upsd 2>/dev/null
         echo "done"
        echo
    fi
}        

install()
{
    disp_title
    echo "*** Installation for Linux ***"
    echo
    echo "The default destination directory is" /usr/local/bulldog "."
    echo "Enter your new destination directory below, "
    echo "or just press 'Enter' key for default."
    echo -n "New destination directory: "
    read newpath
    if [ "$newpath" = "" ]
    then
        INSTALL_PATH="/usr/local/bulldog"
    else
        INSTALL_PATH=$newpath
    fi
    if [ ! -d $INSTALL_PATH ]
    then
        mkdir -p $INSTALL_PATH
    fi
    chmod u+wrx,go+rx-w $INSTALL_PATH
    echo $INSTALL_PATH > /etc/upsd.path
    set_Master_Slave
    echo
    echo -n "Copying files ."
    /bin/cp ./monitor $INSTALL_PATH
    delay
    /bin/cp ./upsd $INSTALL_PATH
    delay
    /bin/cp ./configure $INSTALL_PATH
    delay
#    /bin/cp ./S99bulldog $INSTALL_PATH
#    delay
#    /bin/ln -s $INSTALL_PATH/S99bulldog /etc/rc.d/rc3.d 2>/dev/null
#    delay
#    /bin/ln -s $INSTALL_PATH/S99bulldog /etc/rc.d/rc5.d 2>/dev/null
#    delay
#    /bin/cp ./uninstall $INSTALL_PATH 
#    delay
    /bin/cp ./Command.Shutdown $INSTALL_PATH
    delay
    /bin/cp ./Command.Mail $INSTALL_PATH
    delay
#    /bin/cp ./Command.Wall $INSTALL_PATH
#    delay
    /bin/cp ./Command.Write $INSTALL_PATH
    delay
#    /bin/cp ./check $INSTALL_PATH
#    delay
    /bin/cp ./libupshttp.so /usr/lib
    delay
    if [ ! -d $INSTALL_PATH/WWWRoot ]
    then
        mkdir -p $INSTALL_PATH/WWWRoot
    fi
    chmod u+wrx,go+rx-w $INSTALL_PATH/WWWRoot
    /bin/cp ./WWWRoot/* $INSTALL_PATH/WWWRoot
    chmod u+wr-x,go+r-wx $INSTALL_PATH/WWWRoot/*
    delay
    if [ ! -d $INSTALL_PATH/icons ]
    then
        mkdir -p $INSTALL_PATH/icons
    fi
    chmod u+wrx,go+rx-w $INSTALL_PATH/icons
    /bin/cp ./icons/* $INSTALL_PATH/icons
    chmod u+wr-x,go+r-wx $INSTALL_PATH/icons/*
    delay
    if [ ! -d $INSTALL_PATH/help ]
    then
        mkdir -p $INSTALL_PATH/help
    fi
    chmod u+wrx,go+rx-w $INSTALL_PATH/help
    /bin/cp ./help/* $INSTALL_PATH/help
    chmod u+wr-x,go+r-wx $INSTALL_PATH/help/*
    delay
    chmod u+wrx,go-wrx $INSTALL_PATH/monitor
    delay
    chmod u+wrx,go-wrx $INSTALL_PATH/upsd
    delay
    chmod u+wrx,go-wrx $INSTALL_PATH/configure
    delay
    chmod u+wrx,go-wrx $INSTALL_PATH/uninstall
    delay
#    chmod u+wrx,go-wrx $INSTALL_PATH/S99bulldog
#    delay
    chmod u+wrx,go-wrx $INSTALL_PATH/Command.Shutdown
    delay
    chmod u+wrx,go-wrx $INSTALL_PATH/Command.Mail
    delay
#    chmod u+wrx,go-wrx $INSTALL_PATH/Command.Wall
#    delay
    chmod u+wrx,go-wrx $INSTALL_PATH/Command.Write
    delay
#    chmod u+wrx,go-wrx $INSTALL_PATH/check
#    delay
    chmod u+wrx,go-wrx /usr/lib/libupshttp.so
    delay
    echo
    ./chkpas $INSTALL_PATH
    echo
    echo
    echo "Installation complete."
    echo
    echo "Programs have been installed in the $INSTALL_PATH."
    echo
}        
    
disp_menu()
{
    echo "*** Installation for Linux ***"
    echo
    echo -n "Do you want to install the Belkin Bulldog Plus now ?[y|n] "
    read answer
    if [ $answer = "y" ]
    then
        install
    else
        echo "Bye !"
        exit
    fi
}

clear_files()
{
    rm -f ./Command.Mail
    rm -f ./Command.Write
#    rm -f ./Command.Wall
    rm -f ./Command.Shutdown
    rm -f ./check
    rm -f ./S99bulldog
    rm -f ./install
    rm -f ./uninstall
    rm -rf ./WWWRoot
    rm -rf ./icons
    rm -rf ./help
    rm -f ./upsd
    rm -f ./monitor
    rm -f ./configure
    rm -f ./chkpas
    rm -f ./libupshttp.so
}
    
#######################################
# main loop
#######################################
check_user
check_exist
disp_title
disp_menu

temp="path=$INSTALL_PATH"
ed - S99bulldog <<! > /dev/null
/path
a
$temp
.
1;
/path
d
w
q
!

/bin/cp ./S99bulldog $INSTALL_PATH
chmod u+wrx,go-wrx $INSTALL_PATH/S99bulldog
/bin/ln -s $INSTALL_PATH/S99bulldog /etc/rc.d/rc3.d 2>/dev/null
/bin/ln -s $INSTALL_PATH/S99bulldog /etc/rc.d/rc5.d 2>/dev/null

#Change uninstall path
ed - uninstall <<! > /dev/null
/path
a
$temp
.
1;
/path
d
w
q
!

/bin/cp ./uninstall $INSTALL_PATH 
chmod u+wrx,go-wrx $INSTALL_PATH/uninstall

#Change check path
ed - check <<! > /dev/null
/path
a
$temp
.
1;
/path
d
w
q
!

/bin/cp ./check $INSTALL_PATH
chmod u+wrx,go-wrx $INSTALL_PATH/check

start_upsd
clear_files
[/FONT]
[URL="https://www.cyberciti.biz/faq/debian-ubuntu-centos-rhel-install-apcups/"]


[/URL]

---

