---
title: "Touchscreen &quot;greentouch&quot; under ubuntu server or 16.04"
date: 2017-08-21
forum: Hardware
---

### Post by moratorro on 2017-08-21
Hi All:

[COLOR=#333333][FONT=Arial]Hi all:[/FONT][/COLOR]

[COLOR=#333333][FONT=Arial]im having a nightmare time trying to install the touchscreen drivers from greentouch on a ubuntu 16.04 ( i have installed server then desktop on top)[/FONT][/COLOR]

[COLOR=#333333][FONT=Arial]its supposed to be this one: Model Number	GT-TMO185A[/FONT][/COLOR]
and the drivers


[http://www.greentouch.com.cn/products_detail/&productId=158.html](http://www.greentouch.com.cn/products_detail/&productId=158.html)
4 wire Resistive touch screen	Windows 2000,Windows XP,Win 8,Windows NT,Windows CE,Linux,Mac>



[COLOR=#333333][FONT=Arial]once i try to install the touchkit i get this:

[/FONT][/COLOR][FONT=arial]Rebuild the TouchKit driver. ( this is from the manual)[/FONT]
[FONT=arial]3.1) Locate the extracted directory. And go to the subdirectory[/FONT]
[FONT=arial]/touchkit/include then type make new[/FONT]

[FONT=arial]make new[/FONT]
[FONT=arial]rm -f configSTR.h configSTR.mak configINT.h configINT.mak touch.tcl[/FONT]
[FONT=arial]tclsh ../utility/tcl2h.tcl configSTR.tcl > configSTR.h[/FONT]
[FONT=arial]tclsh ../utility/tcl2mak.tcl configSTR.tcl > configSTR.mak[/FONT]
[FONT=arial]tclsh ../utility/tcl2h.tcl configINT.tcl > configINT.h[/FONT]
[FONT=arial]tclsh ../utility/tcl2mak.tcl configINT.tcl > configINT.mak[/FONT]
[FONT=arial]tclsh ../utility/ini2tcl.tcl touch.ini > touch.tcl[/FONT]

[FONT=arial]3.2) change the directory to /touchkit then type make all[/FONT]
[FONT=arial]The touchKit driver will be rebuild. ( Some packages must be[/FONT]
[FONT=arial]installed and well configured[/FONT]

[FONT=arial]for n in include driver utility xf86drv diag usb; do                \[/FONT]
[FONT=arial]    make -C $n || exit 1;        \[/FONT]
[FONT=arial]done[/FONT]
[FONT=arial]make[1]: se entra en el directorio '/home/pos/Escritorio/slepos/[/FONT][FONT=arial]touchscreen/Ubuntu  Kubuntu(for x86)/Ubuntu6.06/touchkit/[/FONT][FONT=arial]include'[/FONT]
[FONT=arial]make[1]: No se hace nada para 'all'.[/FONT]
[FONT=arial]make[1]: se sale del directorio '/home/pos/Escritorio/slepos/[/FONT][FONT=arial]touchscreen/Ubuntu  Kubuntu(for x86)/Ubuntu6.06/touchkit/[/FONT][FONT=arial]include'[/FONT]
[FONT=arial]make[1]: se entra en el directorio '/home/pos/Escritorio/slepos/[/FONT][FONT=arial]touchscreen/Ubuntu  Kubuntu(for x86)/Ubuntu6.06/touchkit/[/FONT][FONT=arial]driver'[/FONT]
[FONT=arial]for t in tpaneld; do                \[/FONT]
[FONT=arial]    if [ -f $t ];  then            \[/FONT]
[FONT=arial]        cp -f $t bin;                \[/FONT]
[FONT=arial]    fi;                                \[/FONT]
[FONT=arial]done[/FONT]
[FONT=arial]make[1]: se sale del directorio '/home/pos/Escritorio/slepos/[/FONT][FONT=arial]touchscreen/Ubuntu  Kubuntu(for x86)/Ubuntu6.06/touchkit/[/FONT][FONT=arial]driver'[/FONT]
[FONT=arial]make[1]: se entra en el directorio '/home/pos/Escritorio/slepos/[/FONT][FONT=arial]touchscreen/Ubuntu  Kubuntu(for x86)/Ubuntu6.06/touchkit/[/FONT][FONT=arial]utility'[/FONT]
[FONT=arial]for t in PanelInfo WriteConf; do                \[/FONT]
[FONT=arial]    if [ -f $t ];  then            \[/FONT]
[FONT=arial]        cp -f $t bin;                \[/FONT]
[FONT=arial]    fi;                                \[/FONT]
[FONT=arial]done[/FONT]
[FONT=arial]make[1]: se sale del directorio '/home/pos/Escritorio/slepos/[/FONT][FONT=arial]touchscreen/Ubuntu  Kubuntu(for x86)/Ubuntu6.06/touchkit/[/FONT][FONT=arial]utility'[/FONT]
[FONT=arial]make[1]: se entra en el directorio '/home/pos/Escritorio/slepos/[/FONT][FONT=arial]touchscreen/Ubuntu  Kubuntu(for x86)/Ubuntu6.06/touchkit/[/FONT][FONT=arial]xf86drv'[/FONT]
[FONT=arial]Makefile:1026: *** missing separator.  Stop.[/FONT]
[FONT=arial]make[1]: se sale del directorio '/home/pos/Escritorio/slepos/[/FONT][FONT=arial]touchscreen/Ubuntu  Kubuntu(for x86)/Ubuntu6.06/touchkit/[/FONT][FONT=arial]xf86drv'[/FONT]
[FONT=arial]Makefile:57: [/FONT]Failure in the instructions for the object[FONT=arial] 'all'[/FONT]
[FONT=arial]make: *** [all] Error 1[/FONT]

[COLOR=#333333][FONT=Arial]i appreciate the help
[/FONT][/COLOR]the ubuntu its is spanish right now, sorry

[COLOR=#333333][FONT=Arial]regards[/FONT][/COLOR]

---

