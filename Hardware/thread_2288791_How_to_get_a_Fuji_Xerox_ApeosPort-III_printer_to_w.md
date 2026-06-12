---
title: "How to get a Fuji Xerox ApeosPort-III printer to work?"
date: 2015-07-29
forum: Hardware
---

### Post by dalekky on 2015-07-29
I want to get my Ubuntu laptop to "talk" with a Fuji Xerox ApeosPort-III C5500 colour digital printer.

I managed to find and download a Linux/GNU [driver installer for it here]("http://onlinesupport.fujixerox.com/processDriverForm.do;jsessionid=13F1D9969494DF481B2132C5FD8AB4CB.worker4?ctry_code=NZ&lang_code=en&d_lang=en&corp_pid=APIIIC5500&rts=null&model=ApeosPort-III+C5500&type_id=2&oslist=GNU+%2F+Linux&lang_list=en"). If that link does not work, it can be found on that page entering "ApeosPort-III C5500" into the search and choosing "Linux / GNU" as the OS, then it takes you to the download page.

It downloads a zip archive filename "UNIX_Driver_4-3-1.zip" which contains further .tar archives in a subfolder "Linux".

Now, I ran the driver installer as per the instructions given in the README file via "sudo ./install.sh"
It placed items into its default locations:
/usr/lib/fxps2428
/usr/local/fxbin2428
/usr/local/fxetc2428

The installer made the following two complaints when installing:
./install.sh: 807: [: -eq: argument expected

and...
install: cannot create regular file ‘/usr/X11R6/lib/X11/app-defaults’: No such file or directory

But other than that, no other errors. So I figured it must have worked.

I went to CUPS to add the printer.... could not find the printer name listed ANYWHERE when choosing the driver for it. Not under Fuji Xerox, not under Xerox... no where.
So where has the driver gone?

I can't use a PPD file because the only PPD files I can find for this printer are for MacOS

This laptop is running Ubuntu 15.04

---

### Post by dalekky on 2015-07-30
I've since also found an RPM package and source files on this Japanese Fuji Xerox page - [http://www.fujixerox.co.jp/download/apeosport/download/c4300series/linux/](http://www.fujixerox.co.jp/download/apeosport/download/c4300series/linux/)

However, this is another dead end for me because:
1. I can't convert the RPM to a DEB package with alien because it complains that I can't build a 32bit package on a 64bit OS; and
2. I can't build from the source files because it is giving me errors I can't figure out with my limited knowledge.

For anyone who thinks they can work out why it won't build, below is the output from "make" command:
```
dalek@dalek-Inspiron-3520:~/Downloads/fxlinuxprint-src-1.0.1$ make
gcc  -g -O2   -o pstopdffx -lcups pstopdffx-fxlinuxprint.o pstopdffx-codec.o  
pstopdffx-fxlinuxprint.o: In function `fxGetPrintOptions':
/home/dalek/Downloads/fxlinuxprint-src-1.0.1/fxlinuxprint.c:377: undefined reference to `cupsGetDests'
/home/dalek/Downloads/fxlinuxprint-src-1.0.1/fxlinuxprint.c:378: undefined reference to `cupsGetDest'
/home/dalek/Downloads/fxlinuxprint-src-1.0.1/fxlinuxprint.c:379: undefined reference to `cupsGetPPD'
/home/dalek/Downloads/fxlinuxprint-src-1.0.1/fxlinuxprint.c:381: undefined reference to `cupsFreeDests'
/home/dalek/Downloads/fxlinuxprint-src-1.0.1/fxlinuxprint.c:385: undefined reference to `cupsParseOptions'
/home/dalek/Downloads/fxlinuxprint-src-1.0.1/fxlinuxprint.c:387: undefined reference to `ppdOpenFile'
/home/dalek/Downloads/fxlinuxprint-src-1.0.1/fxlinuxprint.c:388: undefined reference to `ppdMarkDefaults'
/home/dalek/Downloads/fxlinuxprint-src-1.0.1/fxlinuxprint.c:389: undefined reference to `cupsMarkOptions'
/home/dalek/Downloads/fxlinuxprint-src-1.0.1/fxlinuxprint.c:394: undefined reference to `ppdFindMarkedChoice'
/home/dalek/Downloads/fxlinuxprint-src-1.0.1/fxlinuxprint.c:441: undefined reference to `ppdClose'
/home/dalek/Downloads/fxlinuxprint-src-1.0.1/fxlinuxprint.c:443: undefined reference to `cupsFreeOptions'
collect2: error: ld returned 1 exit status
Makefile:248: recipe for target 'pstopdffx' failed
make: *** [pstopdffx] Error 1
```

---

### Post by dalekky on 2015-08-03
bump!

I really need help with getting either of these to work.
Do I need to post more information?
Surely someone more knowledgeable can figure out where I am going wrong with installing?

---

### Post by dalekky on 2015-08-04
Here is contents of the install.sh file in my original post.
Apparently there is something wrong with the syntax.

If anyone can spot the error, please reply! Thanks. CLUE - line 807 gives an "argument expected" error

```
#!/bin/sh
#
# @(#)install.sh.m4 1.0 04/04/02 XSSC
#
# Installed System software for Fuji Xerox AP Printers.
#
copyright="Copyright(C) 2009 by Fuji Xerox Asia Pacific Pte Ltd. All rights reserved."
progtitle="FXAP UNIX Driver Installer for Redhat Linux"
progname="$0"
PATH=/usr/ucb:/bin:/etc:/usr/bin:/usr/etc:/usr/sbin
# Setup default parameters
PrinterName=""
HOSTNAME=""         # net install host name
TAPEDEV="/dev/fd0"
REWIND=""
#### directorys ###
ROOT=
CURDIR="`pwd`"
SAVEDIR="`pwd`/SAVED"
## DocuCentre C400 Series
PACKAGE400="uxdriver.tar"
BINDIR400="${ROOT}/usr/local/fxbinC400"
LIBDIR400="${ROOT}/usr/lib/fxpsC400"
ETCDIR400="${ROOT}/usr/local/fxetcC400"
## DocuPrint C2428 Series
PACKAGE2428="uxdriver2.tar"
BINDIR2428="${ROOT}/usr/local/fxbin2428"
LIBDIR2428="${ROOT}/usr/lib/fxps2428"
ETCDIR2428="${ROOT}/usr/local/fxetc2428"
## DocuCentre-II C3000 Series
PACKAGE3000="uxdriver3.tar"
BINDIR3000="${ROOT}/usr/local/fxbin3000"
LIBDIR3000="${ROOT}/usr/lib/fxps3000"
ETCDIR3000="${ROOT}/usr/local/fxetc3000"
##
SAMPLEDIR="${ROOT}/usr/local/fxsrc"
MANDIR="${ROOT}/usr/man/ja_JP.ujis"
MANDIR2="${ROOT}/usr/man/ja_JP.eucJP"
MANDIRF="${ROOT}/usr/share/man/ja"
PRINTCAP="${ROOT}/etc/printcap"
TERMINFO="${ROOT}/usr/share/lib/terminfo"
MODEL_PATH="${ROOT}/usr/lib/lp/model"
ETC="${ROOT}/etc"
RESOURCEDIR="${ROOT}/usr/X11R6/lib/X11/app-defaults"
### utility for installation ###
bins="euc2ps2 fxoption tiff2ps2 xwd2ps2"
libs="fxpof fxoption_exec string_from_printcap fxbanner.ps fxpif_sample.sh"
printcap="printcap.add"
filter="fxpif fxpof fxpvf fxpg4f"
filter_add="A3 A4"
## DocuPrint C400 Series
defaults400=".fxpsdefaultC400"
man1400="euc2psC2400.1 fxoptionC400.1 fxpifC400.1 fxpofC400.1 fxpvfC400.1 fxpg4fC400.1 tiff2ps2C400.1 tiff2g4C400.1 xwd2ps2C400.1 xwd2g4C400.1"
man5400="fxpsdefaultC400.5"
## DocuPrint C2428 Series
defaults2428=".fxpsdefault2428"
man12428="euc2ps22428.1 fxoption2428.1 fxpif2428.1 fxpof2428.1 fxpvf2428.1 fxpg4f2428.1 tiff2ps22428.1 tiff2g42428.1 xwd2ps22428.1 xwd2g42428.1"
man52428="fxpsdefault2428.5"
## DocuCentre-II C3000 Series
defaults3000=".fxpsdefault3000"
man13000="euc2ps23000.1 fxoption3000.1 fxpif3000.1 fxpof3000.1 fxpvf3000.1 fxpg4f3000.1 tiff2ps23000.1 tiff2g43000.1 xwd2ps23000.1 xwd2g43000.1"
man52428="fxpsdefault3000.5"
## GUI Tool
bins_gui="ufptool"
bins_gui5="ufptool5"
bins_gui7="ufptool7"
bins_gui_file=".UFPDefault"
resource_gui_file="Ufptool"

################################
## Printer Model Registration ##
################################
RegisterPrinterModels() {
     Model DCC400        FXDCC400.fd     "Document Centre C240/C320/C400"
     Model DPC2428       FXDPC2428.fd    "DocuPrint C2428"
     Model DCC450        FXDCC450.fd     "Document Centre  C450/C360/C250"
     Model APC6550       FXAPC6550.fd    "ApeosPort C6550 I/C5540 I"
     Model DCC6550       FXDCC6550.fd    "DocuCentre C6550 I/C5540 I"
     Model AP2C4300      FXAP2C4300.fd   "ApeosPort-II C4300/C3300/C2200"
     Model DC2C4300      FXDC2C4300.fd   "DocuCentre-II C4300/C3300/C2200"
     Model DC2C3000      FXDC2C3000.fd   "DocuCentre-II C3000"
     Model AP2C7500      FXAP2C7500.fd   "ApeosPort-II C7500/C6500/C5400"
     Model DC2C7500      FXDC2C7500.fd   "DocuCentre-II C7500/C6500/C5400"
     Model AP3C3300      FXAP3C3300.fd   "ApeosPort-III C2201/C2200/C3300"
     Model DC3C3300      FXDC3C3300.fd   "DocuCentre-III C2201/C2200/C3300"
     Model AP3C4400      FXAP3C4400.fd   "ApeosPort-III C4400"
     Model DC3C4400      FXDC3C4400.fd   "DocuCentre-III C4400"
     Model AP3C7600      FXAP3C7600.fd   "ApeosPort-III C7600/C6500/C5500"
     Model DC3C7600      FXDC3C7600.fd   "DocuCentre-III C7600/C6500/C5500"
     Model BinaryInstall2428     dummy2428.fd   "Binary update only"
} #EndRegisterPrinterModels
# model_pt<n> ... printer model name
# model_fd<n> ... Solaris FD file name
# model_mn<n> ... menu string
Model() {
    [ x"$ModelCount" = x ] && ModelCount=0
    eval ModelCount=`expr $ModelCount + 1`
    eval model_pt$ModelCount=$1
    eval model_fd$ModelCount=$2
    eval model_mn$ModelCount="\"$3\""
    eval fd_$1=$2
}
## Display Model Selet Menu
ModelSelectMenu() {
    echo "Please wait..."
    RegisterPrinterModels
    clear
    echo "$progtitle"
    echo "$copyright"
    echo ""
    echo "Printer Model?"
    i=1
    tmp=$i
    menustr=x
    while [ x"$menustr" != xExit ]
    do
        eval menustr="\"\$model_mn$i\""
        [ $i -gt $ModelCount ] && menustr="Exit"
        echo "  ${i}. $menustr"
        [ $i -gt 1 ] && tmp="${tmp}/${i}"
        i=`expr $i + 1`
    done
    i=""
    while [ "`expr $i + 0 2>&1`" != "$i" ]
    do
        echo -n "Enter Process No(${tmp})?:"
        read i
    done
    if [ $i -gt $ModelCount ]
    then
        EJECT
        exit
    fi
    eval PrinterName=\$model_pt$i
    if [ "`P400check`" = "true" ]
    then
        PACKAGE=$PACKAGE400
        BINDIR=$BINDIR400
        LIBDIR=$LIBDIR400
        defaults=$defaults400
        ETCDIR=$ETCDIR400
        man1=$man1400
        man5=$man5400
    elif [ "`P2428check`" = "true" ]
    then
        PACKAGE=$PACKAGE2428
        BINDIR=$BINDIR2428
        LIBDIR=$LIBDIR2428
        defaults=$defaults2428
        ETCDIR=$ETCDIR2428
        man1=$man12428
        man5=$man52428
    elif [ "`P3000check`" = "true" ]
    then
        PACKAGE=$PACKAGE3000
        BINDIR=$BINDIR3000
        LIBDIR=$LIBDIR3000
        defaults=$defaults3000
        ETCDIR=$ETCDIR3000
        man1=$man13000
        man5=$man53000
    fi
}
### DocuPrint C400 Series Check ###
P400check() {
   if [ "${PrinterName}" = "DCC400" ]
    then
        echo "true"     # DocuCentre Color 400/320/240/160 Series
    else
        echo "false"    # Not DocuPrint C400 Series
    fi
}
### DocuPrint C2428 Series Check ###
P2428check() {
    if [ "${PrinterName}" = "DPC2428" ]
    then
        echo "true"     # DocuPrint C2428 Series
    elif [ "${PrinterName}" = "DCC450" ]
    then
        echo "true"     # Document Centre C450/C360/C250 Series
    elif [ "${PrinterName}" = "APC6550" ]
    then
        echo "true"     # ApeosPort C6550 I/C5540 I Series
    elif [ "${PrinterName}" = "DCC6550" ]
    then
        echo "true"     # DocuCentre C6550 I/C5540 I Series
    elif [ "${PrinterName}" = "AP2C4300" ]
    then
        echo "true"     # ApeosPort-II C4300/C3300/C2200 Series
    elif [ "${PrinterName}" = "DC2C4300" ]
    then
        echo "true"     # DocuCentre-II C4300/C3300/C2200 Series
    elif [ "${PrinterName}" = "AP2C7500" ]
    then
        echo "true"     # ApeosPort-II C7500/C6500/C5400 Series
    elif [ "${PrinterName}" = "DC2C7500" ]
    then
        echo "true"     # DocuCentre-II C7500/C6500/C5400 Series
    elif [ "${PrinterName}" = "AP3C3300" ]
    then
        echo "true"     # ApeosPort-III C2201/C2200/C3300 Series
    elif [ "${PrinterName}" = "DC3C3300" ]
    then
        echo "true"     # DocuCentre-III C2201/C2200/C3300 Series
    elif [ "${PrinterName}" = "AP3C4400" ]
    then
        echo "true"     # ApeosPort-III C4400 Series
    elif [ "${PrinterName}" = "DC3C4400" ]
    then
        echo "true"     # DocuCentre-III C4400 Series
    elif [ "${PrinterName}" = "AP3C7600" ]
    then
        echo "true"     # ApeosPort-III C7600/C6500/C5500 Series
    elif [ "${PrinterName}" = "DC3C7600" ]
    then
        echo "true"     # DocuCentre-III C7600/C6500/C5500 Series
    elif [ "${PrinterName}" = "BinaryInstall2428" ]
    then
        echo "true"     # BinaryInstall
    else
        echo "false"    # Not DocuPrint C2428 Series
    fi
}
### DocuCentre-II C3000 Series Check ###
P3000check() {
   if [ "${PrinterName}" = "DC2C3000" ]
    then
        echo "true"     # DocuCentre-II C3000 Series
    else
        echo "false"    # Not DocuCentre-II C3000 Series
    fi
}
################################
# Local functions
#
### turn off MSI/MailBox/Sorter
CutOff() {
    egrep -v 'MSI|m1|m2|m3|m4|m5|m6|m7|m8|m9|m10|Ost' $1
}
### get OS Major Version ###
OSMVersion() {
    uname -r | awk '{printf ("%s",1)}'
}
### get OS Version ###
OSVersion() {
    uname -r | awk '{printf ("%s",1)}'
}
### nlecho message ###
nlecho() {
    echo
    echo $*
}
### errorexit exitcode message ###
errorexit() {
    nlecho "$progname:$2" 1>&2
    ${EJECT}
    echo
    exit $1
}
### readparam message default_value
readparam() {
    if [ "$2" = "" ]
    then
        echo
        echo -n "$1:"
        read parameter
    else
        echo
        echo -n "$1[$2]:"
        read parameter
        parameter="${parameter:-$2}"
    fi
}
### readenum message default_value
readenum() {
    parameter=""
    while [ "${parameter}" = "" ]
    do
        echo
        echo -n "$1(1:$2 2:$3):"
        read parameter
        if [ "${parameter}" = "1" ]
        then
            parameter="$2"
        elif [ "${parameter}" = "2" ]
        then
            parameter="$3"
        else
            parameter=""
        fi
    done
}
### ask 'y' or 'n' ###
YesNo() {
    ans=""
    case "$2" in
        Yes|y)
            dmsg="y"
            ;;
        No|n)
            dmsg="n"
            ;;
        *)
            dmsg=""
            ;;
    esac
    while [ "$ans" = "" ]
    do
        echo
        echo -n "$1(y/n)${dmsg:+[$dmsg]}:"
        read ans
        ans="${ans:-$dmsg}"
        if [ "$ans" = "y" -o "$ans" = "n" ]
        then
            return
        fi
        echo "You must select 'y' or 'n'."
        ans=""
    done
}
### Menu ###
Menu() {
    n=$#
    i=1
    tmp=$i
    while [ $i -le $n ]
    do
        echo "  ${i}. $1"
        if [ $i -gt 1 ]
        then
            tmp="${tmp}/${i}"
        fi
        eval param_$i="\"$1\""
        shift
        i=`expr $i + 1`
    done
    i=""
    while [ "`expr $i + 0 2>&1`" != "$i" ]
    do
        echo -n "Enter Process No(${tmp})?:"
        read i
    done
    eval ans=\$param_"$i"
    return $i
}
### Extract ###
Extract() {
    install_directory=$1
    shift 1
    install_Zfiles=""
    install_files=""
    for f in $*
    do
        if ((found "${bins_solaris}" ${f}) && [ "`OSMVersion`" = "5" ])
        then
            install_Zfiles="${install_Zfiles} ${f}5.Z"
        else
            install_Zfiles="${install_Zfiles} $f.Z"
        fi
        install_files="${install_files} $f"
    done
    ${REWIND}
    cwd=`pwd`
    cd ${CURDIR}
    tar xvf ${TAPEDEV} ${install_Zfiles}
    for f in ${install_files}
    do
        gunzip ${f}
        install -g bin -o root $f ${install_directory}
        /bin/rm ${CURDIR}/$f
    done
    cd $cwd
}
### filename ###
filename() {
    set `echo $1 | sed 's/\// /g'`
    shift `expr $# - 1`
    echo $1
}
### found ###
found() {
    for i in $1
    do
        if [ "${i}" = $2 ]
        then
            return 0
        fi
    done
    return 1
}
### keyedit edit_file key addfile saved ###
keyedit() {
    echo -n "   $1 ... "
    RC=255
    grep "$2" $1 >/dev/null 2>&1
    case "$?" in
        0)
            echo "already edited."
            ;;
        2)
            echo "file not found."
            ;;
        1)
            if [ ! -f "$4/`filename $1`" ]
            then
                cp $1 $4
                RC=0
            fi
            if [ -w $1 ]
            then
                cat $3 >> $1 2>/dev/null
                echo "done"
            else
                echo "Permission denied."
            fi
            ;;
    esac
    return ${RC}
}
### read parameter with confirm ###
ReadParamWithConfirm() {
    parameter=""
    while [ "${parameter}" = "" ]
    do
        readparam "Enter $1?" "$2"
        if [ "$#" = "2" ]
        then
            YesNo "$1 is '${parameter}'" "y"
            if [ "$ans" = "n" ]
            then
                parameter=""
            fi
        elif [ $3 ${parameter} ]
        then
            parameter=""
        fi
    done
}
### read printer name with confirm ###
ReadPrinterNameWithConfirm() {
    parameter=""
    while [ "${parameter}" = "" ]
    do
        readparam "Enter $1?" "$2"
        if (echo ${parameter} | grep "[^a-zA-Z0-9_]")
        then
            echo "$1 can only contain alphanumeric characters and underscores"
            parameter=""
        else
            if [ "`echo -n ${parameter} | wc -c`" -le 14 ]
            then
                YesNo "$1 is '${parameter}'" "y"
                if [ "$ans" = "n" ]
                then
                    parameter=""
                fi
            else
                echo "$1 exceeds 14 characters"
                parameter=""
            fi
        fi
    done
}
##
mk_LIBDIR() {
    ### disk free space check
    df
    echo
    echo "This Software requires at least 20MB disk space."
    echo "Enter a new directory at the following prompt,if you want change the path."
    LINKDIR=""
    WORKPARAM=""
    OK="n"
    while [ "${LINKDIR}" = "" ]
    do
        while [ "${OK}" = "n" ]
        do
            readparam "Enter directory name" "${LIBDIR}"
            if [ `expr substr ${parameter} 1 1` != "/" ]
            then
                YesNo "directory is '`pwd`/${parameter}'  " n
                WORKPARAM="`pwd`/${parameter}"
            else
                YesNo "directory is '${parameter}'  " n
                WORKPARAM="${parameter}"
            fi
            OK=${ans}
        done
        LINKDIR="${WORKPARAM}"
        if [ -d ${LINKDIR} ]
        then
            echo "'${LINKDIR}' already exists."
            YesNo "Erase ${libs} ${defaults} in '${LINKDIR}'. Confirm?" n
            if [ "$ans" = "y" ]
            then
                dir=`pwd`
                echo -n "'delete..."
                cd ${LINKDIR}
                rm -rf ${libs} UserDefault/${defaults}
                cd ${dir}
                echo "done"
            #else
            #   LINKDIR=""
            fi
        fi
    done
    if [ "${LINKDIR}" != "${LIBDIR}" ]
    then
        mkdir ${LINKDIR}
        ln -s ${LINKDIR} ${LIBDIR}
    else
        [ ! -d $LIBDIR ] && mkdir $LIBDIR
    fi
    set `df ${LIBDIR} | grep -v Filesystem`  # RedHat8 ÂÐ±þ
    FREE="$4"
    FILESYS="$6"
    if [ ${FREE:=0} -lt 1024 ]
    then
        nlecho "Not enough space in '${FILESYS}' file system."
        rm -rf ${LIBDIR} ${LINKDIR}
        errorexit 255 "Installation aborted."
    fi
}
### Make binary install directry
mk_BINDIR() {
    LINKBDIR=""
    WORKPARAM=""
    OK="n"
    while [ "${LINKBDIR}" = "" ]
    do
        while [ "${OK}" = "n" ]
        do
            readparam "Enter binary directory name" "${BINDIR}"
            if [ `expr substr ${parameter} 1 1` != "/" ]
            then
                YesNo "directory is '`pwd`/${parameter}'  " n
                WORKPARAM="`pwd`/${parameter}"
            else
                YesNo "directory is '${parameter}'  " n
                WORKPARAM="${parameter}"
            fi
            OK=${ans}
        done
        LINKBDIR="${WORKPARAM}"
        if [ -d ${LINKBDIR} ]
        then
            echo "'${LINKBDIR}' already exists."
            YesNo "Erase ${bins_solaris} ${bins_gui} in '${LINKBDIR}'. Confirm?" n
            if [ "$ans" = "y" ]
            then
                dir=`pwd`
                echo -n "'delete..."
                cd ${LINKBDIR}
                rm -rf ${bins_solaris} ${bins_gui}
                cd ${dir}
                echo "done"
            fi
        fi
        if [ -d ${LINKBDIR}/UFPDefault ]
        then
            echo "'${LINKBDIR}/UFPDefault' already exists."
            YesNo "Erase ${bins_gui_file} in '${LINKBDIR}/UFPDefault'. Confirm?" n
            if [ "$ans" = "y" ]
            then
                dir=`pwd`
                echo -n "'delete..."
                cd ${LINKBDIR}
                rm -rf ${bins_gui_file}
                cd ${dir}
                echo "done"
            fi
        fi
    done
    if [ "${LINKBDIR}" != "${BINDIR}" ]
    then
        mkdir ${LINKBDIR}
        BINDIR="${LINKBDIR}"
    else
        [ ! -d $BINDIR ] && mkdir $BINDIR
    fi
    set `df ${BINDIR} | grep -v Filesystem`  # RedHat8 ÂÐ±þ
    FREE="$4"
    FILESYS="$6"
    if [ ${FREE:=0} -lt 5120 ]
    then
        nlecho "Not enough space in '${FILESYS}' file system."
        rm -rf ${LINKBDIR}
        errorexit 255 "Installation aborted."
    fi
}

#Clean library install directory for binary update
mk_UD_LIBDIR() {
    ### disk free space check
    echo "Enter library and binary installed directory."
    LINKDIR=""
    OK="n"
    while [ "${LINKDIR}" = "" ]
    do
        while [ "${OK}" = "n" ]
        do
            readparam "Enter library directory name" "${LIBDIR}"
            if [ `expr substr ${parameter} 1 1` != "/" ]
            then
                YesNo "directory is '`pwd`/${parameter}'  " n
            else
                YesNo "directory is '${parameter}'  " n
            fi
            OK=${ans}
        done
        LINKDIR="${parameter}"
        if [ -d ${LINKDIR} ]
        then
            dir=`pwd`
            echo -n "'Delete all old library files..."
            cd ${LINKDIR}
            rm -rf ${libs}
            cd ${dir}
            echo "done"
        else
            echo "Directory not found."
            echo "Binary update give up."
            exit 255
        fi
    done
}

#Clean binary install directory for binary update
mk_UD_BINDIR() {
    LINKBDIR=""
    WORKPARAM=""
    OK="n"
    while [ "${LINKBDIR}" = "" ]
    do
        while [ "${OK}" = "n" ]
        do
            readparam "Enter binary directory name" "${BINDIR}"
            if [ `expr substr ${parameter} 1 1` != "/" ]
            then
                YesNo "directory is '`pwd`/${parameter}'  " n
                WORKPARAM="`pwd`/${parameter}"
            else
                YesNo "directory is '${parameter}'  " n
                WORKPARAM="${parameter}"
            fi
            OK=${ans}
        done
        LINKBDIR="${WORKPARAM}"
        if [ -d ${LINKBDIR} ]
        then
            dir=`pwd`
            echo -n "'Delete all old binary files..."
            cd ${LINKBDIR}
            rm -rf ${bins}
            rm -rf ${bins_gui}
            cd ${dir}
        else
            echo "Directory not found."
            echo "Binary update give up."
            exit 255
        fi
        if [ -d ${LINKBDIR}/UFPDefault ]
        then
            dir=`pwd`
            cd ${LINKBDIR}
            rm -rf ${bins_gui_file}
            cd ${dir}
            echo "done"
        fi
    done
}

#Make etc install directry
mk_ETCDIR() {
    LINKEDIR=""
    WORKPARAM=""
    OK="n"
    while [ "${LINKEDIR}" = "" ]
    do
        while [ "${OK}" = "n" ]
        do
            readparam "Enter etc directory name" "${ETCDIR}"
            if [ `expr substr ${parameter} 1 1` != "/" ]
            then
                YesNo "directory is '`pwd`/${parameter}'  " n
                WORKPARAM="`pwd`/${parameter}"
            else
                YesNo "directory is '${parameter}'  " n
                WORKPARAM="${parameter}"
            fi
            OK=${ans}
        done
        LINKEDIR="${WORKPARAM}"
        if [ -d ${LINKEDIR} ]
        then
            echo "'${LINKEDIR}' already exists."
            YesNo "Erase ${printcap} in '${LINKEDIR}'. Confirm?" n
            if [ "$ans" = "y" ]
            then
                dir=`pwd`
                echo -n "'delete..."
                cd ${LINKEDIR}
                rm -rf ${printcap}
                cd ${dir}
                echo "done"
            fi
        fi
    done
    if [ "${LINKEDIR}" != "${ETCDIR}" ]
    then
        mkdir ${LINKEDIR}
        ETCDIR="${LINKEDIR}"
    else
        [ ! -d $ETCDIR ] && mkdir $ETCDIR
    fi
    set `df ${ETCDIR} | grep -v Filesystem`  # RedHat8 ÂÐ±þ
    FREE="$4"
    FILESYS="$6"
    if [ ${FREE:=0} -lt 6144 ]
    then
        nlecho "Not enough space in '${FILESYS}' file system."
        rm -rf ${LINKEDIR}
        errorexit 255 "Installation aborted."
    fi
}
### do symbolic link ###
LN_S() {
    [ -f $2 ] && rm -f $2   # remove, if $2 already exists.
    ln -s $1 $2
}
### do hard link ###
LN_H() {
    [ -f $2 ] && rm -f $2   # remove, if $2 already exists.
    ln $1 $2
}
### Linux Install ###
Linux_Install() {
    YesNo "Install Filters?" "y"
    if [ "$ans" = "y" ]
    then
        mk_LIBDIR
        mk_BINDIR
        mk_ETCDIR
        install -d -m 755 ${BINDIR}
        install -d -m 755 ${LIBDIR}
        install -d -m 755 ${LIBDIR}/UserDefault
        install -d -m 755 ${ETCDIR}
        install -d -m 755 ${BINDIR}/UFPDefault
        Extract ${LIBDIR} ${libs}
        Extract ${LIBDIR}/UserDefault ${defaults}
        Extract ${BINDIR} ${bins}
        RVER=`uname -r | awk '{printf ("%s",substr($1,5,2))}'`
        MVER=`uname -r | awk '{printf ("%s",substr($1,3,1))}'`
        eval MNUM=\$MVER #MinerVersion
        eval RNUM=\$RVER #Revision
        #if Kernel Ver 2.0.xx
        if [ 0 -eq $MNUM ]
        then
            #if Kernel Ver 2.0.36 upper
            if [ 35 -lt $RNUM ]
            then
                tar xvf ${TAPEDEV} ${bins_gui5}.Z
                gunzip ${bins_gui5}.Z
                install -g bin -o root ${bins_gui5} ${BINDIR}/${bins_gui}
                /bin/rm ${CURDIR}/${bins_gui5}
            else
                Extract ${BINDIR} ${bins_gui}
            fi
        #if Kernel Ver 2.2.xx
        elif [ 2 -eq $MNUM ]
        then
            GMVER=`rpm -q glibc | awk '{printf ("%s",substr($1,9,1))}'`
            GRVERT=`rpm -q glibc | awk '{printf ("%s",substr($1,12,1))}'`
            if [ "-" == $GRVERT ]
            then
                GRVER=`rpm -q glibc | awk '{printf ("%s",substr($1,11,1))}'`
            else
                GRVER=`rpm -q glibc | awk '{printf ("%s",substr($1,11,2))}'`
            fi
            eval GMNUM=\$GMVER
            eval GRNUM=\$GRVER
            #if glibc Ver 2.2.xx
            if [ 2 -eq $GMNUM ]
            then
                tar xvf ${TAPEDEV} ${bins_gui7}.Z
                gunzip ${bins_gui7}.Z
                install -g bin -o root ${bins_gui7} ${BINDIR}/${bins_gui}
                rm ${CURDIR}/${bins_gui7}
            #if glibc Ver 2.1.95 upper
            elif [ 94 -lt $GRNUM ]
            then
                tar xvf ${TAPEDEV} ${bins_gui7}.Z
                gunzip ${bins_gui7}.Z
                install -g bin -o root ${bins_gui7} ${BINDIR}/${bins_gui}
                rm ${CURDIR}/${bins_gui7}
            else
                tar xvf ${TAPEDEV} ${bins_gui5}.Z
                gunzip ${bins_gui5}.Z
                install -g bin -o root ${bins_gui5} ${BINDIR}/${bins_gui}
                /bin/rm ${CURDIR}/${bins_gui5}
            fi
        #if Kernel Ver 2.x.xx
        else
            GMVER=`rpm -q glibc | awk '{printf ("%s",substr($1,9,1))}'`
            eval GMNUM=\$GMVER
            #if glibc Ver 2.1.xx
            if [ 1 -eq $GMNUM ]
            then
                tar xvf ${TAPEDEV} ${bins_gui5}.Z
                gunzip ${bins_gui5}.Z
                install -g bin -o root ${bins_gui5} ${BINDIR}/${bins_gui}
                /bin/rm ${CURDIR}/${bins_gui5}
            #if glibc Ver 2.2.xx upper
            else
                tar xvf ${TAPEDEV} ${bins_gui7}.Z
                gunzip ${bins_gui7}.Z
                install -g bin -o root ${bins_gui7} ${BINDIR}/${bins_gui}
                rm ${CURDIR}/${bins_gui7}
            fi
        fi
        Extract ${BINDIR}/UFPDefault ${bins_gui_file}
        Extract ${RESOURCEDIR} ${resource_gui_file}
        Extract ${ETCDIR} ${printcap}
#        if [ -d ${MANDIRF} ]
#        then
#            MANDIR="${MANDIRF}"
#        elif [ -d ${MANDIR2} ]
#        then
#            LN_S ${MANDIR2} ${MANDIR}
#        fi
#        Extract ${MANDIR}/man1 ${man1}
#        Extract ${MANDIR}/man5 ${man5}
        ## compatibility
#        if [ "`P400check`" = "true" ]
#        then
#            cd $MANDIR/man5
#            LN_S fxpsdefault400.5 .fxpsdefault400.5
#        elif [ "`P2428check`" = "true" ]
#        then
#            cd $MANDIR/man5
#            LN_S fxpsdefault2428.5 .fxpsdefault2428.5
#        else
#            cd $MANDIR/man5
#            LN_S fxpsdefault1250.5 .fxpsdefault1250.5
#        fi
        # do binary hard link
        LN_H ${BINDIR}/euc2ps2 ${LIBDIR}/fxpif
        LN_H ${BINDIR}/xwd2ps2 ${LIBDIR}/fxpvf
        LN_H ${BINDIR}/xwd2ps2 ${LIBDIR}/fxpg4f
        LN_H ${BINDIR}/xwd2ps2 ${BINDIR}/xwd2g4
        LN_H ${BINDIR}/tiff2ps2 ${BINDIR}/tiff2g4
        cd ${LIBDIR}
        for i in ${filter_add}
        do
            for j in ${filter}
            do
                LN_S ${j} ${j}_${i}
            done
        done
        echo
        echo "*** Editing ${PrinterName} Enviroment files. ***"
        echo
        if [ "`P400check`" = "true" ]
        then
            MTYPE="C400"
        elif [ "`P2428check`" = "true" ]
        then
            MTYPE="2428"
        elif [ "`P3000check`" = "true" ]
        then
            MTYPE="3000"
        fi
        if keyedit ${PRINTCAP} fxps${MTYPE}/fxpif ${ETCDIR}/${printcap} ${SAVEDIR}
        then
            SAVE_FILES="${SAVE_FILES} ${PRINTCAP}"
        fi
        echo "${BINDIR}" > /tmp/fxbinpath${MTYPE}
        install -g bin -o root /tmp/fxbinpath${MTYPE} ${LIBDIR}
        rm -f /tmp/fxbinpath${MTYPE}
    fi
    echo
    if [ "${SAVE_FILES}" ]
    then
        echo ${SAVE_FILES} | tr -s ' ' '\012'
        echo "Original files is saved in '${SAVEDIR}'."
    else
        rm -r ${SAVEDIR}
    fi
}

### Linux Binary Install ###
Linux_BinaryInstall() {
    YesNo "Update Binaries?" "y"
    if [ "$ans" = "y" ]
    then
        mk_UD_LIBDIR
        mk_UD_BINDIR
        install -d -m 755 ${BINDIR}
        install -d -m 755 ${BINDIR}/UFPDefault
        install -d -m 755 ${LIBDIR}
        Extract ${LIBDIR} ${libs}
        Extract ${BINDIR} ${bins}
        RVER=`uname -r | awk '{printf ("%s",substr($1,5,2))}'`
        MVER=`uname -r | awk '{printf ("%s",substr($1,3,1))}'`
        eval MNUM=\$MVER #MinerVersion
        eval RNUM=\$RVER #Revision
        #if Kernel Ver 2.0.xx
        if [ 0 -eq $MNUM ]
        then
            #if Kernel Ver 2.0.36 upper
            if [ 35 -lt $RNUM ]
            then
                tar xvf ${TAPEDEV} ${bins_gui5}.Z
                uncompress ${bins_gui5}.Z
                install -g bin -o root ${bins_gui5} ${BINDIR}/${bins_gui}
                /bin/rm ${CURDIR}/${bins_gui5}
            else
                Extract ${BINDIR} ${bins_gui}
            fi
        #if Kernel Ver 2.2.xx
        elif [ 2 -eq $MNUM ]
        then
            GMVER=`rpm -q glibc | awk '{printf ("%s",substr($1,9,1))}'`
            GRVERT=`rpm -q glibc | awk '{printf ("%s",substr($1,12,1))}'`
            if [ "-" == $GRVERT ]
            then
                GRVER=`rpm -q glibc | awk '{printf ("%s",substr($1,11,1))}'`
            else
                GRVER=`rpm -q glibc | awk '{printf ("%s",substr($1,11,2))}'`
            fi
            eval GMNUM=\$GMVER
            eval GRNUM=\$GRVER
            #if glibc Ver 2.2.xx
            if [ 2 -eq $GMNUM ]
            then
                tar xvf ${TAPEDEV} ${bins_gui7}.Z
                uncompress ${bins_gui7}.Z
                install -g bin -o root ${bins_gui7} ${BINDIR}/${bins_gui}
                rm ${CURDIR}/${bins_gui7}
            #if glibc Ver 2.1.95 upper
            elif [ 94 -lt $GRNUM ]
            then
                tar xvf ${TAPEDEV} ${bins_gui7}.Z
                uncompress ${bins_gui7}.Z
                install -g bin -o root ${bins_gui7} ${BINDIR}/${bins_gui}
                rm ${CURDIR}/${bins_gui7}
            else
                tar xvf ${TAPEDEV} ${bins_gui5}.Z
                uncompress ${bins_gui5}.Z
                install -g bin -o root ${bins_gui5} ${BINDIR}/${bins_gui}
                /bin/rm ${CURDIR}/${bins_gui5}
            fi
        #if Kernel Ver 2.x.xx
        else
            GMVER=`rpm -q glibc | awk '{printf ("%s",substr($1,9,1))}'`
            eval GMNUM=\$GMVER
            #if glibc Ver 2.1.xx
            if [ 1 -eq $GMNUM ]
            then
                tar xvf ${TAPEDEV} ${bins_gui5}.Z
                uncompress ${bins_gui5}.Z
                install -g bin -o root ${bins_gui5} ${BINDIR}/${bins_gui}
                /bin/rm ${CURDIR}/${bins_gui5}
            #if glibc Ver 2.2.xx upper
            else
                tar xvf ${TAPEDEV} ${bins_gui7}.Z
                uncompress ${bins_gui7}.Z
                install -g bin -o root ${bins_gui7} ${BINDIR}/${bins_gui}
                rm ${CURDIR}/${bins_gui7}
            fi
        fi
        Extract ${BINDIR}/UFPDefault ${bins_gui_file}
        Extract ${RESOURCEDIR} ${resource_gui_file}
#        if [ -d ${MANDIRF} ]
#        then
#            MANDIR="${MANDIRF}"
#        elif [ -d ${MANDIR2} ]
#        then
#            LN_S ${MANDIR2} ${MANDIR}
#        fi
#        Extract ${MANDIR}/man1 ${man1}
#        Extract ${MANDIR}/man5 ${man5}
        ## compatibility
#        if [ "`P3530check`" = "true" ]
#        then
#            cd $MANDIR/man5
#            LN_S fxpsdefault3320.5 .fxpsdefault3320.5
#        elif [ "`P2220check`" = "true" ]
#        then
#            cd $MANDIR/man5
#            LN_S fxpsdefault2220.5 .fxpsdefault2220.5
#        elif [ "`P3530check`" = "true" ]
#        then
#            cd $MANDIR/man5
#            LN_S fxpsdefault3530.5 .fxpsdefault3530.5
#        else
#            cd $MANDIR/man5
#            LN_S fxpsdefault1250.5 .fxpsdefault1250.5
#        fi
        # do binary hard link
        LN_H ${BINDIR}/euc2ps2 ${LIBDIR}/fxpif
        LN_H ${BINDIR}/xwd2ps2 ${LIBDIR}/fxpvf
        LN_H ${BINDIR}/xwd2ps2 ${LIBDIR}/fxpg4f
        LN_H ${BINDIR}/xwd2ps2 ${BINDIR}/xwd2g4
        LN_H ${BINDIR}/tiff2ps2 ${BINDIR}/tiff2g4
        cd ${LIBDIR}
        for i in ${filter_add}
        do
            for j in ${filter}
            do
                LN_S ${j} ${j}_${i}
            done
        done
        if [ "`P400check`" = "true" ]
        then
            MTYPE="C400"
        elif [ "`P2428check`" = "true" ]
        then
            MTYPE="2428"
        elif [ "`P3000check`" = "true" ]
        then
            MTYPE="3000"
        fi
        echo "${BINDIR}" > /tmp/fxbinpath${MTYPE}
        install -g bin -o root /tmp/fxbinpath${MTYPE} ${LIBDIR}
        rm -f /tmp/fxbinpath${MTYPE}
    fi
}

### Eject floppy ###
EJECT() {
    echo
}
##
setup_tapedevice() {
    if [ $?PACKAGE ]
    then
        if [ -f $PACKAGE ]
        then
            TAPEDEV=$PACKAGE
        else
            echo
            echo "Extracting a package, please wait..."
            tar xf $TAPEDEV $PACKAGE 2>&1 >/dev/null
            [ -f $PACKAGE ] && TAPEDEV=$PACKAGE
        fi
    fi  # if no package found, old version of Unix Filter
}
################################
# START Installation Here
################################
#/usr/ucb/clear
if [ "`whoami`" != "root" ]
then
    errorexit 255 "should be used by 'root'."
fi
if [ ! -d ${SAVEDIR} ]
then
    mkdir ${SAVEDIR}
fi
SAVE_FILES=""
ModelSelectMenu
setup_tapedevice
if [ ! -d ${ETC} ]
then
    mkdir ${ETC}
fi
if [ ! -f ${PRINTCAP} ]
then
    Extract ${ETC} printcap_hed
    cd /etc
    mv printcap_hed printcap
    chmod 644 printcap
fi
if [ ! "$PrinterName" = "BinaryInstall2428" ]; then
    Linux_Install
else
    Linux_BinaryInstall
fi
awk -F : '{print $1 " " $6}' /etc/passwd > ${LIBDIR}/UserDefault/.userhomedir
chmod 755 ${LIBDIR}/UserDefault/.userhomedir
##[ -f $PACKAGE ] && rm -f $PACKAGE
echo ""
echo "done."
##EJECT
##### END-OF-INSTALL #####
```

---

### Post by dalekky on 2016-02-16
bump...

Is there anything at all that can be done to make this printer talk to ubuntu?

---

