---
title: "Help to install a .desktop file"
date: 2008-08-27
forum: General Help
---

### Post by KillerKellerjr on 2008-08-27
Hello - I am rather new to the Ubuntu Linux world and need a little help with installing the Bomgar Representative software on my home PC, trying to get away from Windows 100% at home.  I need this to support my work's clients when I am on 24hr support.  Currently Bomgar's website ([http://www.bomgar.com/linux/linuxquestions.htm](http://www.bomgar.com/linux/linuxquestions.htm)) states they support Suse Linux for the representative but Initial testing has shown that both Bomgar's representative and customer clients are stable on other distros, maybe meaning Ubuntu?

I have successfully logged into my work's Bomgar login site and have the option to download the linux version.  So I downloaded the file, it is in Bomgar.desktop format and Bomgar's site states to download it to the desktop and then just click on it to launch it.  When I do that I get an error but can't recall since I am at work right now.

Does anyone know what a file is with a .desktop extension?  I tried to see if it was a packaged file but I can't unzip it...not sure how to figure it out.  Any help would be greatly appreciated.  Do I need to install something?

---

### Post by ajgreeny on 2008-08-27
You are probably dealing with either an rpm package which is for suse and other rpm distros or perhaps the .desktop file is a script file of some sort and needs to be made executable.  Try right clicking on it and in the permissions tab of the properties, change it to executable.

I have to say I have no idea of this program at all and nor do I have any knowledge of .desktop files, other than the small files for icons on the desktop, ie the links to programs on the machine, so do proceed with caution as I may have got it completely wrong.

---

### Post by KillerKellerjr on 2008-08-27
Changing it to execute did not work, it still errored with "There was an error launching the application."

I did find this by right clicking and selecting the Launcher tab in the command line:

bash "-c" "exec echo bash \'"%k"\' | sed -e 's!file://!!' | sh"

but the other two fields were blank.  I hope that makes some sense to someone.  I think I will use Firefox's useragent switcher to act like I am Windows to download the Windows client and see if it installs and works with WINE.  If that works then it will be good enough since I am only on support a couple times a year.

---

### Post by KillerKellerjr on 2008-08-27
Besides actually remoting into a client, Bomgar seems to install and run under WINE.  I was able to login and it shows all other employees that were currently signed into the system so I assume it is working 100%.  I will find out this weekend when I go On-Call.

I believe I will report that on the WINE APPDB for other to benefit and give up on installing the Suse Linux version unless I can figure out how to rip it appart and recompile it or whatever I need to do.

Thanks and let me know if you have any other ideas

---

### Post by rpalmertree on 2008-08-28
> **KillerKellerjr said:**
> Hello - I am rather new to the Ubuntu Linux world and need a little help with installing the Bomgar Representative software on my home PC, trying to get away from Windows 100% at home.  I need this to support my work's clients when I am on 24hr support.  Currently Bomgar's website ([http://www.bomgar.com/linux/linuxquestions.htm](http://www.bomgar.com/linux/linuxquestions.htm)) states they support Suse Linux for the representative but Initial testing has shown that both Bomgar's representative and customer clients are stable on other distros, maybe meaning Ubuntu?

I have successfully logged into my work's Bomgar login site and have the option to download the linux version.  So I downloaded the file, it is in Bomgar.desktop format and Bomgar's site states to download it to the desktop and then just click on it to launch it.  When I do that I get an error but can't recall since I am at work right now.

Does anyone know what a file is with a .desktop extension?  I tried to see if it was a packaged file but I can't unzip it...not sure how to figure it out.  Any help would be greatly appreciated.  Do I need to install something?

First what version of Bomgar is your company using?  There was a known incompatibility with Bomgar 10.0.x and Ubuntu 8.04, the issue is the version of Gnome hardy uses is different than what the customer/rep client recognize.

In the past when I could not get the rep client running, I have had to change the executable bit on the .desktop file.  Outside of that you should be able to use this method to get an error message.

{

Open terminal
type 'cd ~/Desktop' (where ever you downloaded it to)
type 'sh bomgar-<blah>'

}

If this gives an error message there is likely a problem with the Bomgar version your running, I would suggest contacting support about it.

---

### Post by flickerfly on 2008-10-29
Here's the error when I get when I try to install. I talked to a rep of bomgar who suggested that it was a probem with dependencies. This doesn't seem to make sense to me, but...

```
$ sh bomgar-rep-installer.desktop 
bomgar-rep-installer.desktop: 1: [Desktop: not found
bomgar-rep-installer.desktop: 4: Representative: not found
bomgar-rep-installer.desktop: 6: -c: not found
bomgar-rep-installer.desktop: 8: GenericName[en_US]=: not found
bomgar-rep-installer.desktop: 10: [X-Bomgar: not found

```

here's what the top of the .desktop file has in it before it goes binary on me.

```
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Bomgar Representative Client Installer
Terminal=false
Exec=bash "-c" "exec echo bash \\'"%k"\\' | sed -e 's!file://!!' | sh"
Type=Application
GenericName[en_US]=

[X-Bomgar Installer]
tempfile=${TMPDIR:-${TEMP:-${TEMPDIR:-${TMP:-/tmp}}}}/bomgar-rep.$$ l=. exit $es
DESKTOP_INSTALLER=$(cd "$(dirname "$0")"; pwd)/$(basename "$0") "$tempfile" "$@" es=$?
```

I understand that this can be installed. I had a previous version installed on Ubuntu without any problems, but this is a new version and it seems to come with a new problem.

---

### Post by jrasmussen0 on 2008-10-29
To get bomgar.com to install on Ubuntu Intrepid 64-bit follow these steps.

1. Download the *.desktop file from Bomgar
2. Change permissions on the file through Nautilus so that you can execute the file
3. If you get the error "error while loading shared libraries: libpng.so.3" then you need to double check /usr/lib/libpng* AND /usr/lib32/libpng* for a libpng.so.3.  This is a 32-bit program so 64-bit users will have to look at the /usr/lib32 directory.
   a. if you don't have the file you can create a symbolic link
   b. sudo ln -s libpng.so.0.27 /usr/lib32/libpng.so.3
4. The second error I got was "That DESKTOP_INSTALLER" variable is not set"
   a. Bomgar's only use for the variable seems to be to rm -f "$DESKTOP_INSTALLER" to remove the installer file
   b. export DESKTOP_INSTALLER=/tmp/bomgar-rep.1410  #or a dummy file to sacrifice if you want to keep the installer.

---

### Post by Wayne_V on 2008-10-29
The .desktop file is not an executable -- it is a config file that defines a launcher for the desktop.   Just drop the .desktop file in ~/Desktop and then you should see an icon on the desktop that says "_Bomgar Representative Client Installer"_.  Double click to launch.

---

### Post by flickerfly on 2008-10-29
Wayne_V, it surely must contain an executable because in previous versions something's run and it is more than just a text file.

My problem is that it won't run. Running it on the shell was just an attempt to figure out why.

More precisely (now that I'm back to this computer) the error reads, 

> There was an error launching the application.

I don't seem to have a way of getting more information out of it.

---

### Post by Wayne_V on 2008-10-30
flickerfly - it may contain a bash script but the snippet you show is a .desktop launcher.   The command it runs is: 

Exec=bash "-c" "exec echo bash \\'"%k"\\' | sed -e 's!file://!!' | sh"

Try placing the file in ~/Desktop  -- you should see an Icon for launching the installer then.

---

### Post by flickerfly on 2008-10-30
> **Wayne_V said:**
> flickerfly - it may contain a bash script but the snippet you show is a .desktop launcher.   The command it runs is: 

Exec=bash "-c" "exec echo bash \\'"%k"\\' | sed -e 's!file://!!' | sh"

Try placing the file in ~/Desktop  -- you should see an Icon for launching the installer then.

Yeah, I have the file sitting on the Desktop. I minimize all my windows and then double-click the file. That's when I get the error in a window that pops up that says simply "There was an error launching the application." I get that you're suppose to just click on it and it work, the problem is that it doesn't. (This paragraph might come across as a little rude. I don't mean it that way, just trying to be clear.) :)

I've also tried taking the bash command apart so I can try to run it by hand, but I haven't been successful in that. I don't know what exec echo bash \\'"%k"\\' is accomplishing. I can't find a reference to %k anywhere in the man pages for bash or echo. I suppose it is trying to match a pattern of some sort for \"something"\ to feed to sed, but I don't know what the something is so I can't manually feed it to sed or figure out where it gets the data.

---

### Post by Wayne_V on 2008-10-30
OK - missed that part.   %k is the URI of the launcher itself (see [http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s06.html](http://standards.freedesktop.org/desktop-entry-spec/latest/ar01s06.html))

So it looks like it is piping "bash file.desktop" to "sh".   

What is the binary in the file?   Can you send the "head -30" and maybe "tail -10" from the .desktop file?

---

### Post by flickerfly on 2008-10-31
Here's the stuff you mentioned needing to debug it further. Thanks for the documentation to further understand the %k stuff. That's very helpful for me to play with.

```
~/Desktop$ head -30 bomgar-rep-installer.desktop 
[Desktop Entry]
Version=1.0
Encoding=UTF-8
Name=Bomgar Representative Client Installer
Terminal=false
Exec=bash "-c" "exec echo bash \\'"%k"\\' | sed -e 's!file://!!' | sh"
Type=Application
GenericName[en_US]=

[X-Bomgar Installer]
tempfile=${TMPDIR:-${TEMP:-${TEMPDIR:-${TMP:-/tmp}}}}/bomgar-rep.$$
l=. exit $es
DESKTOP_INSTALLER=$(cd "$(dirname "$0")"; pwd)/$(basename "$0") "$tempfile" "$@"
es=$?
&#65533;&&#65533;G=&#65533;S&#65533;v7&#65533;X$&#65533;&#903;&#65533;&#65533;&#65533;'&#65533;j&#65533;**\\&#65533;H&#65533;&#65533;&#65533;w*}zE&#65533;&#65533;&#65533;&#65533;
                                           &#65533;&#65533;&#65533;&#65533;&#65533;M&#65533;&#65533;.&#65533;T&#65533;"&#65533;&#65533;4&#65533;(&#65533;&#65533;p&#953;&#65533;&#65533;9XuGfb`&#65533;&#65533;&#65533;kD/&#65533;JL&#65533;&#65533;&#65533;c&#65533;&#65533;\t(U&#65533;d&#65533;&#65533;&#65533;&#65533;0&#65533;L&#65533;&#65533;&#31279;&#65533;~g&#65533;&#65533;&#1840;&#65533;&#65533;&&#65533;&#65533;&#65533;T &#65533;&#65533;e&#65533;&#65533;(&#65533;P&#65533;&#65533;&#65533;)P&#65533;&#65533;&#1508;&#65533;&#65533;g]3&#65533;&#65533;R&#65533;&#65533;&#65533;:&#65533;C&#65533;x&#65533;J&#65533;
                                                                                                                                                                      .v&#65533;&#65533;&#65533;&#24023;&#65533;&#65533;&#65533;&#65533;)&#65533;r&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#336;&‹&#65533;&#65533;&#65533;q&#65533;&#65533;[W^&#65533;JNG|&#65533;&#65533;^]c&#65533;&#65533;]X}&#65533;6#Y&#65533;&#65533;$&#65533;&#65533;a&#65533;{&#1832;&#65533;V&#65533;v&#65533;&#65533;5j&#65533;&#65533;&#65533;&#65533;'x}&#65533;bV&#65533;&#65533;q&#65533;&#65533;&#65533;&#65533;&#65533;t(~/!Jp&#65533;/&#65533;&#65533;P&#65533;&#65533;&#36184;7&#65533;d&#65533;=&#65533;7W&#65533;vT&#65533;&#65533;f&#65533;&#65533;*&#65533;&#65533;1)7&#65533;4S&#65533;&#65533;&#65533;'&#65533;<&#65533;&#65533;=&#65533;^&#65533;w&#65533;8&#65533;J&#65533;&#65533;&#65533;M&#65533;P&#336;&#65533;e&#730;&#65533;m&#65533;_d&#34769;&#65533;Q&#65533;/#&#348;&#65533;/&#65533;&#1820;&#65533;&#1599;&#65533;lO&#65533;H7'f83)&#65428;&#65533;&#65533;&#65533;T&#1919;&#65533;K&#65533;/=55 &#65533;RS&#65533;L&#65533;HK
                 &#65533;&#65533;/=E&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;4&#65533;O&#65533;$&#65533;&#65533;&#65533;+&#65533;&#65533;Z1&#65533;&#65533;&#65533;&#65533;-&#65533;:f6&#65533;WV&#65533;r;&#65533;&#65533;&#65533;&#65533;K&#65533;/pH&#16361;&#65533;6g&#65533;&#65533;W&#65533;&#65533;!&#933;&#65533;&#65533;\\\t5
&#65533;&#65533;
  &#65533;hq&#401;&#65533;&#65533;_&#65533;o&#65533;&#65533;&&#65533;&#65533;&#65533;%&#65533;&#65533;%&#65533;G&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;kC&#65533;&#314676;s&#65533;&#65533;&#65533;&#65533;&#65533;t%&#65533;n&#65533;&#65533;'&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;\K&#65533;&#65533;&M&#65533;&#65533;&#65533;a&#65533;&#65533;:&#65533;&#65533;&#65533;&#65533;&#65533;=uhS&#65533;<U&#65533;&#65533;&#65533;&#65533;X]w]7]&#65533;
&#65533;oe&#65533;Yo&#65533;&#65533;&#65533;h&#65533;K&#65533;w&#65533;&#65533;v&#65533;)d=}&#65533;&#65533;O&#65533;-d&#65533;k)&#65533;aOg&#65533;Xo&#65533;?o&#65533;>w&#65533;:&#65533;
                                                    &#65533;&#65533;b-&#65533;N-&#65533;y&#65533;i&#65533;&#65533;8x60e?7&#65533;=&#65533;R&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
y
 &#65533;&#65533;5&#65533;&#65533;b;&#65533;&#65533;&#65533;{&#65533;N7&#65533;&#65533;G S ck1t&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;=(&#65533;+l&#65533;XC&#65533;&#65533;&#65533;u&#2023;&#65533;^<&#65533;QV&#65533;z&#65533;&#65533;o&#65533;&#65533;x1L&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;O&#65533;&#65533;&#1694;&#65533;<&#65533;?&#1245;F-)&#997;&#806;,&#1065;&#65533;&#65533;&#65533;&#879;&#32092;&#65533;@?&#65533;&#65533;&#65533;J&#65533;~&#65533;s&#65533;]dP&#65533;8&#65533;}_&#65533;}&#65533;3&#65533;u&#65533;&#65533;Tt`&#65533;7&#65533;w1p/&#65533;&#65533;&#65533;&#65533;E=G&#65533;O\t&#65533;/&#65533;&#1239;h&#65533;&#65533;&#65533;l&#65533;3B|;h&#65533;&#65533;(&#1300;&#65533;`&#65533;.&#65533;&#1699;&#65533;
                                                                                                                                                                                  
&#65533;&#760;Kh&#65533;i|&#65533;ht=P&#65533;&#65533;7&#65533;Mt&#65533;xh&#65533;&#65533;&#65533;&#1327;&#65533;&#1299;&#65533;>T&#65533;I&#65533;&#65533;&#65533;M&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;~&#65533;.&#65533;)M&#65533;ub&#65533;&#65533;Y&#65533;K&#65533;s&#65533;xW/N@&#65533;&#65533;&#65533;3 3&#65533;Ek)x&#65533;&#65533;&#65533;&#65533;S&#65533;[&#65533;3&#65533;&#65533;\t&#65533;&#65533;&#65533;nl?M&#65533;&#65533;z&#65533;;&#65533;&#65533;x&#65533;&#65533; 'B&#65533;b&#65533;«E€WÇBžù&#9149;€Ï&#9227;&#9225;ü@ì×Ðç&#9472;È«5¾âSÛ#ä?
&#9670;¨&#9474;¯Ö*ì0èG!&#960;ˆ;:ä&#9149;À“â®’û&#960;À&#9146;R€Í@W&#9670;€°¬ùôÏBÙµ½ÈÛCÎFY
                                                    £C&#9148;™3äåF&#9670;=ì—Ñï ºž&#9148;-¤ò+Ô¹€&#9226;Ë€°à&#9226;š¾ôü'÷×(Ù_ø´A½/ØÏ¹¬ã‚ü&#9226;…ä—@ß&#9500;ŸÔ°¼-&#9229;°D¼ã€±Ä»&#9484;£!'*N:ÐOÔCÙB ]ÌŸ¦&#9146;×B/=À4ø+À&#9147;‘úMï&#9618;Ô£”Ã€*è«E›Ð&#9146;€ìHÛ&#9149;Œ£
É/á&#8800;ï"—ßœ&#9229;¾£Ìÿäï71&#65533;&#65533;S&#65533;~&#65533;&#65533;xm&#65533;&#65533;&#65533;K&#65533;&#65533;&#65533;&#65533;r&#65533;&#65533;&#65533;~&#65533;N&#65533;Q&#65533;&#65533;&#65533;=&#65533;&#65533;&#65533;&?I&#65533;&#65533;?&#65533;s&#65533;&#65533;&#65533;&#65533;&#65533;~&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;g?&#65533;&#65533;m&#65533;o&#65533;N&#65533;r~&#65533;&#65533;gyG&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;œ&#65533;!&#65533;&#65533;&#65533;D&#1455;#&#65533;&#65533;&#65533;&#1503;&#65533;&#65533;&#65533;&#65533;&#65533;X&#65533;_&#30526;&#65533;y'&#65533;&#65533;&#65533;&#65533;Ka&#65533;&#65533;e|&#65533;&#65533;K&#65533;3&#65533;&#65533;r&#65533;k&#65533;_&#65533;<&#65533;&#65533;|=+&#65533;K&#65533;&#65533;&#65533;x&#65533;&#65533;&#65533;D&#65533;&#65533;&#65533;
&#65533;of&#65533;&#65533;7w&#65533;&#65533;&#65533;ZQ&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;!&#65533;&#65533;Gr<&#65533;&#65533;9&#65533;&#65533;O&#65533;A&#65533;&#65533;&#65533;k&#65533;q&#65533;&#65533;>&#65533;&#65533;'&#65533;`&#65533;X&#65423;&#65533;r=&#65533;"&#65533;&#65533;&#65533;&#65533;}&#65533; &#65533;/d>&#65533;&#65533;&#65533;sZ&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;\\&#65533;&#65533;&#65533;/&#65533;&#65533;O&#65533;&#65533;S&#65533;=&#65533;&#65533;$&#65533;&#65533;?&#65533;&#65533;&#65533;#2&#65533;%&#65533;&#65533;&#65533;&#65533;r9/3&#65533;M&#65533;]O&#65533;'&#416;&#65533;&#65533;W&#65533;&#65533;&#65533;&#65533;~&#65533;Q&#65533;&#65533;n"&#1747;&#65533;&#65533; &#65533;'&#63191;&#65533;&#65533;V~&#65533;Z&#65533;&#65533;&#65533;&#65533;g&#65533;&#65533;C&#65533;&#65533;l?&#65533;&#65533;&#65533;&#65533;y*&#975;&#65533;!&#983;Z&#65423;&#65533;&#65533;&#65533;$&#65533;|M&#65533;~&#65533;e&#65533;&#65533;&#65533;&#65533;&#65533;R&#65533;&#65533;&#65533;&#65533;}&#65533;)&#65533;_e&#65533;&#65533;_&#65533;&#2029;&#65533;z&#65533;jW&#65533;&#65533;&#65533;&#1431;&#65533;'V&#65533;_&#65533;&#65533;&#65533;&#65533;O&#781785;v&#65533;|&#65533;&#65533;&#65533;]&#65533;O?N&#65533; &#65533;Wr&#65533;D&#65533;&#65533;&#65533;Q>&#65533;Ns=&#65533;&#65533;&#65533;z&#65533;&#65533;U&#65533;?&#65533;&#65533;d=y&#65533;/&#65533;|g&#65533;&#65533;&#65533;u&#65533;y*&#65533;Ne&#65533;&#65533;d&#65533;&#65533;2&#65533;}&#65533;&#65533;&#65533;+&#65533;~&#1815;&#65533;m<&#65533;&#65533;&#65533;|l&#65533;z&#2026;&#65533;&#65533;Y_>&#65533;&#65533;&#65533;û÷û&#9149;þ
çã³¡&#9146;¹ßØ°2?&#9492;Áß&#9492;Ê&#9516;ÿžÉŸYð¿Ÿ&#9618;½ô_Ÿ…ù¹Õ&#8804;&#8805;òŽé^ÜîÂú1‚ßÀ÷<ðÿæO†=¼\&#9500;þ&#8804;6àHêì&#960;3èË£ë€b&#65533;(
&#65533;&#65533;C&#65533;s&#65533;O`~&#65533;&#65533;W&#831;&#65533;&#65533;&#65533;&#65533;7&#65533;>&#65533;>&#65533;Q&#65533;&#65533;Y&#65533;&#65533;-&#65533;&#65533;&#65533;&#65533;1&#65533;&#65533;&#65533;&#65533;=&#65533;&#65533;&#65533;&#65533;!&#65533;&#65533;-&#65533;&#65533;&#65533;tz^&#65533;?&#65533;&#65533;?&#65533;H&#65533;&#65533;&#65533;Q&#37513;
~&#65533;<&#65533;
    &#65533;o &#65533;&#65533;&#65533;&#65533;~b&#65533;Cg&#65533;&#65533;&#65533; !ÿß&#65533;&#65533;/&#65533;&#65533;~&#65533;r&#65533;&#65533;Q&#65533;=&#65533;Q&#65533;&#2042;&#65533;h&#65533;~Ao&#65533;&#65533;E&#65533;C&#1975;&#65533;&#65533;V&#65533;ow&#65533;&#2047;&#65533;&#65533;&#608;'&#65533;&#65533;wP&#65533;&#65533;<&#1987;&#65533;&#65533;&#65533;9&#65533;L&#65533;&#65533;a9
&#65533;&#65533;&#65533;&#65533;&#65533;y&#65533;*&#1043;&#65533;&#65533;&#65533;&#65533;x&#65533;&#65533;}&#65533;u4&#65533;&#65533;&#65533;&#65533;&#65533;=V2&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;I>&#65533;&#65533;&#65533;&#65533;&#65533;)&#65533;)&#65533;s/&#65533;&#65533;1&#65533;m&#65533;#&#65533;&#65533;A&#65533;&#65533;}&#65533;=&#65533;&#65533;&#65533;&#65533;{&#65533;RZz&#65533;&#65533;|O`&#65533;&#65533;&#65533;!&#65533;K>8
                                                                                               &#65533;(&#65533;&#65533;&#65533;X&#65533;6&#65533;&#65533;&#65533;&#65533;_&#65533;&#65533;=&#65533;o&#65533;&#65533;&#65533;&#65533;&#65533;
                                                                                                                       &#65533;/&#65533;&#65533;W
                                                                                                                            &#65533;&#65533; &#65533;Gy&#65533;\t&#65533;K&#65533;&#65533;a&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;_
                                                                                                                                                   &#65533;&#65533;|9&#65533;K&#65533;WY&#65533;
&#65533;&#65533;&#65533;&#65533;&&#65533;&#65533;&#65533;&#1397;&#65533;
           ,&#65533;&#65533;_&#65533;&#65533;Ay?&#65533;q&#65533;C&#591;Gq&#65533; &#65533;W&#65533;?&#1167;~&#65533;/A&#65533;uw)&#65533;ä&#65533;&#65533;&#65533;3&#65533;W&#65533;"?&#65533;=&#65533;<r&#65533;&#65533;&#65533;&#65533;&#65533;S%&#1005;O&#65533;Q&#65533;_&#1139;&#65533;4=&#65533;&#65533;x&#286;U&#1787;q&#65533;&#65533;9&#65533;&#65533;&#65533;&#65533;X&#65533;&#65533;ph&#65533;&#65533;&#65533;&#65533;&#65533;c&#65533;&#65533;&#65533;&#65533;&#65533;J&#65533;&#65533;V=&#65533;i&#65533;&#65533;k&#65533;w&#65533;v}(&#65533;&#65533;0&#65533;&#65533;&#65533;&#65533;&#65533;*&#65533;&#65533;b&#65533;G&#65533;&#65533;d&#54963;&#65533;&#65533;&#65533;F&#65533;
"&#1780;&#1908;MI&#65533;&#65533;|/&#65533;t&#65533;Z&#65533;x*&#65533;Q&#65533;)&#65533;T]d&#65533;j&#65533;&#65533;&#1673;+~&#65533;&#65533;&#684;&#65533;&#1137;K&#65533;&#65533;t[&#65533;&#65533;W&#65533;n&#65533;F"S$&#65533;G&#65533;3Q7|&#65533;&#65533;m&#65533;&#65533;"v=&#65533;CVt&#556;L4
Q&#65533;&#65533;&#65533;&#65533;&#65533;)I&#65533;&#65533;8"q&#65533;&#65533;&#932;&#65533;&#65533;E!&#65533;&#65533;&#65533;=&#65533;|&#65533;&#65533;"&#65533;!&#65533;&#65533;u&#65533;bM'&#65533;&#65533;D|6&#65533;&#65533;c&#65533;ÆY&#65533;`R&#65533;!R4&#65533;)CF&#65533;&#65533;&#65533;\t&#65533;6_&#65533;0A&#65533;&#65533;&#65533;-&#65533;k9&#65533;g^U&#1393;&#65533;F
sW
    &#65533;&#65533;&#929;A&#65533;M;&#65533;&#65533;D&#65533;I&#65533;&&#65533;&#65533;*&#65533;&#65533;&#65533;r&#65533;'&#1470;L>-&#65533;K&#65533;i&#65533;^&#65533;&#65533;&#65533;&#65533;&#1731;&#65533;b&#65533;&#65533;DXU&#65533;&#65533;F32&#65533;=&#65533;&#65533;4‰D²Å¡ZË¤HN0Ýú¼^3¦&#9492;‰&#9229;.ÇÕE‡[£€\&#9500;_ûøÿB,&#9532;<AJµI(ãÎ$Eõ!ù['&#9148;ìÛã‡¸Ð«ŒUø×óø±Ë&#8805;³=¯N¬™˜ä^W&#9488;Ñˆ.÷&#9148;æ>ŽKO&#9492;"&#9500;[.é6&#9227;Ê‡‚ &#9484;¸¾&#9492;&#9500;‚+½Ä¿YR)Ò&#9229;*)Iž0þÌ¶ôR7&#65533;"&#65533;&#65533;&#65533;R&#65533;&#1699;Iu:&#1321;E&45&#65533;\\+LDLa&#65533;7&#65533;&&#65533;&#65533;&#65533;&#65533;&#972;&#65533;K&#65533;&#65533;\t&#65533;A&#65533;
                                                                 &#65533;&#65533;&#65533;&#65533;&#65533;i&#65533;&#409;+"F+&#65533;&#65533;u0&#65533;B&#65533;&#65533;&#65533;&#65533;&#65533;>7&#65533;i&#65533;&#65533;& &#65533;C`&#65533;r[3&#65533;&#65533;B&#65533;^re&#65533;1g&#65401;&#65533;E&#65533;(&#65533;N&#788;2q&#65533;&#65533;&#65533;&#65533;&#1643;&#65533;&#65533;$&#65533;I&#65533;&#65533;&#65533;i&#65533;a&#65533;&#65533;I&#65533;V-&#65533;
                                                                                                                                                            %&#65533;&#1628;&#1912;4&#65533;&#65533;&#65533;&#65533;&#65533;0&#65533;f&#2023;&#65533;KF&#65533;&#65533;&#65533;.1I&#65533;g&#65533;&#65533;l&#65533;"g&#65533;&#824;NT^&#65533;Q74&#65533;F+&#1509;h&#1685;&#65533;PF2-]&#65533;>&#1559;a&#65533;$-&#65533;&#65533;&#65533;(GO9&#65533;\tW

```

```
~/Desktop$ tail -10 bomgar-rep-installer.desktop 
-b-&#65533;&#65533;za0&#65533;&#65533;f&#65533;&#65533;&#65533;S&#65533;&#65533;(&#65533;&#65533;&#65533;&#65533;o&#65533;&#65533;&#65533;Y6r&#65533;&#546;&#559;&#65533;w&#65533;&#65533;D&#65533;&#65533;&#582;&#65533;&#65533;&#65533;&#65533;&#294;&#65533;c&#65533;Xs&#1726;&#65533;&#65533;&#65533;&#65533;r=O&#65533;Z}p&#65533;&#65533;[&#65533;&#65533;&#528;&#65533;&#65533;
&#65533;x&#65533;&#65533;J>&#65533;&#65533;i&#65533;&#65533;&#65533;&#65533;\&#65533;&#65533;K&#1003;O+_:&#65533;&#65533;&#65533;RG&#65533;&#65533;R&#65533;&#65533;ey&#65533;&#65533;&#65533;-yyy]&#65533;&#65533;&#65533;&#65533;W&#65533;r]&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;"
                                                               &#65533;&#65533;T&#65533;o&#65533;N&#65533;&#65533;9Z&#65533;G6&#65533;&#65533;=&#1655;&#65533;B&#65533;l{_&#65533;&#4161;&#65533;"&#65533;<I=&#65533;&#65533;®ÌõWÊ±œ£&#9252;,6.&#9149;à*,&#9472;½&#9500;&#9516;Mž&#9488;P¤û®¦OÿK
                                                                                                                                      ÆÎø…Á/*êµèÑ&#9492;§+I¥ú&#9228;£’—îJÄ™°ø®íŸHö&#65533;&#65533;&#65533;;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;,&#65533;&#65533;D&#65533;&#65533;&#65533;h&#65533;&#65533;Ë|&#65533;&#65533;X&#65533;&#65533;&#65533;&#32934;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;db#&#65533;2&#65533;Z&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;cfT&#65533;;Ct&#65533;~
                                                    &#65533;{"&#65533;&#65533;J&#65533;/M&#65533;&#65533;&#542;|&#65533;'&#65533;-&#65533;&#65533;&#65533;&#65533;D&#65533;&#65533;[&#65533;L&#65533;E&#65533;&#65533;{N&#65533;I&#65533;W[~&#65533;c&#65533;h&#65533;d &#65533;2&#65533;NM&#65533;&#318;&#65533;Er&#65533;&#65533;&#65533;N&#65533;@{c&#65533;'&#65533;&#65533;&#65533;[i&#65533;&#65533;&#65533;&#65533;&#65533;aI&#65533;
                                                                                                                                       B:&#65533;&#65533;E4&#65533;&#1818;L&#65533;
                                                                                                                                                  !J&#65533;X}&#65533;&#65533;[k&#65533;&#65533;'D&#65533;&#65533;&#65533;G&#65533;&#65533;&#65533;kU&#65533;&#1479;&#65533;VS&#65533;Z|-)n2G&#65533;&#65533;&#1921;4&#65533;&#65533;&#65533;b
      &#65533;&#65533;&#65533;&#65533;~&#65533;&#65533;P=&#65533;&#65533;*&#533;z&#65533;n7&#65533;&#65533;&#65533;M&#65533;9&#65533;&#65533;\\&#65533;&#65533;&#65533;&#65533;\\S&#65533;&#65533;&#734;&#65533;&#65533;e&#65533;^[&#65533;~&#436;&#65533;.&#65533;Jc&#65533;&#65533;&#65533;&#65533;ZO&#65533;xi
                                                                      rm{&#65533;&#65533;O
                                                                            &#65533;&#65533;Y&#65533;R'&#65533;DST&#65533;k#oMb&#65533;&#65533;zha1&#65533;&#65533; &#65533;@Ny&#65533;&Do&#13343;&#65533;&#65533;&#65533;&#65533;Z&O&#65533;&#920;xG'[U+[Þ36s&#65533;&#65533;wT&#65533;&#65533;r&#65533;uk&#65533;&#466;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;M6&#65533;&#65533;g&#65533;2H&#65533;V&#65533;~&#65533;&#65533;&#65533;N&#65533;&#65533;&#65533;ke&#479;&#65533;z%&#65533;D>&#65533;{&#65533;&#65533;L&#65533;>&#65533;
                  C&#65533;#]&#65533;&#65533;2
ý¥+òÔ™Þë¹·:û§‹®.…'£&#9670;]â¸Ðª‘À›»ÞË¸š&#9618;R¬V¬W¬:W‡*ýZ”&#9516;»Nù©é°ƒ&#9225;›†€¹€ª&#9228;&#9496;ç¾¼&#9227;ƒAƒ÷E´E‡µ&#9226;¥WJ¡÷\
                                                                                          9òŸâ<Šæ3¯Õ[F^Óò,ú\7ýƒ3L&#8800;Û&#9147;ÛýGÑŠ*½U=/Õ0£'›L
                                                                                                                                       ÒÛSæ˜&#9474;Ûð&#9516;=%‹&¥B›&#9500;›«&#9228;Ò&#9496;º&#9226;
&#8805;U’U/8·šOðN¸·º·ðSñ&#9149;ñ&#9488;&#9496;Ï&#9496;Ï±ë&#9488;×Üº£Rë¤VÛëW¯&#9146;¾îËBæÈJôKNçLçôçŒ>¶>&#9500;F´êNU5^ýáä™Û¦óUµ±±0¦…&F±,*TJòJøúž–<-&#9225;.ªÑ¹¬S&#8800;*Ï±éÁ÷ªŽª»ÙLP—V¹W…Ù8Ú&#9472;&#8800;ÜRÚ4¹î&#9148;Ø“°ä&#9492;Yêñƒ
                                                                                                                                                          ÅÇÎ
                                                                                                                                                              ÷£äÃ*£ZúC&#9524;±î¼&#8800;XË&#9148;ÆŒ¸£É¦7ð‰ªƒ/…šó
         &#9148;Þª:&#9472;¬ñ=·”&#9147;>Q3ú%ôª4‡£õ£&#960;Ý¤†ßŠ·ÅÇž•¼œŠœç_ï
                                                     —Í£æçãG®¿B\\º°
Á_’·&#9227;°\‚Ð>É?Ð^‚÷’·3°…•Â*&#9472;ˆÑ„æIíŸý©O
                                         ú/ÖG&#9670;PÒ&#9474;I‚ú„µIÒ&#65533;K&#65533;d//&#65533;=J&&#65533;&#65533;&#65533;&#65533;&#65533;Dl
                                                                                  b&#65533;&#65533;”GK&#9618;@&#8804;&#960;°=4BAò&#65533;K&#65533;H(#&#65533;&#65533;&#65533;N&#65533;$b&#65533;&#65533;I&#65533;;&#65533;&#65533;!&#65533;J$&#65533;&#65533;I&#65533;&#65533;UT$&#65533;&#65533;&#65533;?$Z&#65533;&#65533;&#65533;O&#65533;.E&#65533;&#65533;&#65533;S"2&#65533;&#65533;Gd"
&#65533;&#65533;&#65533;&#65533;?&#65533;&#65533;&#65533;&#65533;&#65533;P&#65533;j&#65533;&#65533; &#65533;D&#65533;QWD&#65533;&#65533;&#65533;&#1102;=&#65533;&#65533;d&#65533;:1&#65533;&#65533;&#65533;k&#65533;Y*&#65533;2kdýM&#65533;_&#553;&#65533;&#65533;&#65533;&#65533;p,\t&#1118;rl'&#65533;vQ&#65533;&#65533;>&#65533;&#65533;&#65533;&#65533;M`]&#65533;lw&#65533;&#65533;&#65533;-&#65533;1&#65533;l]&#65533;)&#65533;&#65533;&#65533;/&#65533;6!OŠS&#960;û³®°¾†æœRŸ·7õã¯³²×ñ&#8805;8·\&#9500;Å&#9149;œ‡F&#9148;\\C÷&#9492;Ã&#65533;&#65533;V&#681;&#1854;&#65533;&#65533;&#65533;&#65533;&#65533;?
                                                                                                                                                        &#65533;zds&#65533;&#65533;&#65533;Fh&#65533;N&#65533;&#65533;%3/j>&#65533;?&#65533;&#65533;&#65533;&#1323;H&#469;&#65533;&#65533;&#65533;K&#65533;-&#65533;Z&#65533;&#65533;&#65533;I{&#65533;
n=\ty&#65533;&#65533;&#1590;1&#931;&#65533;&#65533;&#65533;&#65533;I\\&#65533;Y-×&#65533;&#65533;&#65533;&#65533;]&#65533;"j&#65533;&#65533;Z&#65533;=&#65533;&#65533;&#65533;&#65533;&#935;S&#65533;/&#65533;&#65533;JbxYF&#65533;&#65533;&#65533;q&#65533;a]L</&#65533;&#65533;V&#65533;"&#9472;ï-áƒ…ï¡)êº«M±·È*±¨Y¦£&#8804;—µ.,ŽL
                                                                                                     (Øä&#9496;E¯úJ•:î;«Ã¸ù".áÚ—¨™£–>Mµ“Ë&#9228;&#9484;ã4ÒÜŠ£îÐ>Œ&#9670;Ë&#8804;&<¤œ&#9147;$2ñÅÄ$çZ&#9508;^——¬—ð•ò1±˜žCä‹8&*é°ª*SG·&#9474;Ë¸–—™¡W5]€È›çÈ&#9532;W¿Ÿ0½ÔÎ»;±@£¯ä&#9147;òUýî²\&#9500;»W&#9492;&#9147;C&#8800;›\\+«&#9252;@ÿË÷’&#9148;>ì9ŠøÑS‡W»]œ56¯…É&#9226;°&#9524;¹=¯&#9488;·#G×&#9516;½&#8804;ë9Ý
Û£ö&#65533;&#65533;&#65533;D.&#65533;_&#65533;&#65533;>1&#65533;&#65533;2&#65533;&#65533;&#65533;y&#65533;&#504;&#13091;D&#65533;&#65533;E&#65533;&#65533;@J,ij&#65533;V&#65533;&#65533;&#65533;X))&#65533;&#65533;&#65533;o&#65533;5,&#65533;&#65533;Z[C&#65533;K&#65533;&#65533;&#1446;&#65533;&#65533;/U&#65533;A&#65533;&#65533;&#65533;&#65533;&#65533;&#41584;K&#65533;&#65533;&#65533;&#65533;&#65533;cf%&#65533;&#65533;U(&#65533;&#65533;&#65533;s&#65533;O/&#65533;4&#65533;=&#65533;&#65533;k&#65533;E%v
                                                                                                                 &#65533;T&#65533;&#65533;&#65533;E&#65533;s&#65533;&#65533;&#65533;3;WGO{+_O7g&#65533;&#65533;&#65533;&#65533;&#65533;B&#65533;w&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;oO|&#1104;&#65533;&#1869;$'>7&#65533;&#65533;&#31858;v&#65533;&#65533;$&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;_&#65533;&#65533;&#65533;h&#65533;i&#65533;&#65533;&#65533;m¼
                        AèæÏ[&#9472;&#9508;IA 4@&#9226;Ä€òƒèëŒ¸—YÑ
¢¦&#65533;;&#65533;M&#1153;&#65533;E>&#65533;k&#65533;%&#65533;&#65533;}&#65533;`&#65533;C&#65533;&#65533;&#65533;<&#65533;"&#1402;T&#65533;&#65533;~&#65533;S&#65533;&#65533;&#65533;A&#65533;&#65533;&#65533;r&#65533;&#65533;[c&#1199;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;IH&#65533;&#65533;&#65533;&#65533;hlo&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#1346;&#65533;&#65533;k&#65533;Y&#65533;&#65533;[dC&#65533;&#65533;&#65533;Uv&#65533;&#65533;&#65533;d&#65533;>)6&#65533;&#65533;&#65533;&#65533;&#65533;:&#65533;=&#65533;&#65533;&&#65533;&#65533;&#65533;&#65533;a&#65533;&#65533;&#65533;&#65533;>#&#65533;&#65533;2&#65533;&#65533;~E?&#65533;f&#580;&#65533;‚O&#65533;&#65533;f&#65533;M&#65533;&#65533;&#65533;\\&#65533;&#65533;&#65533;&#65533;&#65533;l>&#65533;&#65533;~\t[&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;K&#1562;[,&#65533;}&#65533;afv&#65533;[&#65533;&#65533;P&#65533;&#65533;`&#65533;&#65533;~&#1488;
&#65533;&#65533;?&#65533;&#65533;&#65533;!S&#65533;&#65533;&#27569;&#5904;&#65533;&#65533;&#65533;&#1605;&#65533;S.&#65533;F&#65533;&#65533;5:%&#65533;F&#65533;cU&#65533;&#65533;0t&#65533;&#65533;&#65533;&#65533;d&#65533;&#65533;Bv&#65533;&#65533;|=*?&#65533;&#65533;&#65533;p&#65533;Z&#65533;SM&#65533;&#65533;$&#65533;&#65533;=&#65533;&#65533;&#65533;&#65533;X&#65533;&#65533;a&#65533;*&#65533;&#65533;O&#65533;K&#65533;&#65533;&#65533;Gv&#65533;&#65533;&#65533;7t/P/&#65533;&#65533;l|O&#65533;&#65533;>ug"4&#65533;&#65533;&&#65533;&#65533;&#65533;&#65533;&#65533;(&#65533;&#65533;$&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;=&#65533;f+‚&#9149;&#9670;#[É¬ÈYU›Ä&#9524;©§‹&#9149;!¶•¤

```

---

### Post by Wayne_V on 2008-10-31
Interesting - I would have expected some sort of tags around the binary so that shell could extract it and do something with it.   Can you try to remove the ASCII from the beginning?  It looks like 12 lines to me (down to the Desktop Installer entry) so 

$ tail +13 (.desktop file) > WhatIsThis

should work - may need to adjust the number of lines if that doesn't remove just the
leading lines.  Or use vi ...

Then do 

$ file WhatIsThis
$ head -c 256 | od -xc

And maybe we can determine what it is.

---

### Post by alienprdkt on 2008-10-31
I can help, well I think.. 

Yesturday I updated to 8.10 and noticed that my hyperspace screensaver was updated, so I tried copy and pasting it to my Mac (didn't really work out as I thought) and it copied as a .desktop file. 

Could it be a screensaver file?

---

### Post by flickerfly on 2008-10-31
from the file command:

gzip compressed data, was "S\3477\222$\252\207\022\250\031\030\353*\\\365\201\356*", last modified: Fri Feb 22 14:47:42 2008

I tried opening this as a gzip file, tar.gzip file and zip file. Each errored out. Example: gzip: bomgar.gz: unexpected end of file

What package is the oc program in? I can't seem to find it and it isn't installed.

---

### Post by flickerfly on 2008-10-31
No, it's definitely a program of some type crammed into a .desktop file. I've run the program before. Support tells me it requires libpng3 and maybe some other stuff, but they don't know what.

---

### Post by Wayne_V on 2008-10-31
sorry - that should be od (for octal dump)

> **flickerfly said:**
> from the file command:

gzip compressed data, was "S\3477\222$\252\207\022\250\031\030\353*\\\365\201\356*", last modified: Fri Feb 22 14:47:42 2008

I tried opening this as a gzip file, tar.gzip file and zip file. Each errored out. Example: gzip: bomgar.gz: unexpected end of file

What package is the oc program in? I can't seem to find it and it isn't installed.

---

### Post by flickerfly on 2008-10-31
In my searching I came across something that may indicate a typo. Is it "od -cx"?

If so:
```

$ head -c 256 bomgar.gz | od -cx
0000000 037 213  \b  \b 336   & 277   G   = 301   S 347   v   7 222   X
        8b1f 0808 26de 47bf c13d e753 3776 5892
0000020   $ 252 316 207 251 022 261 250   ' 031 346 030   j 353   *   *
        aa24 87ce 12a9 a8b1 1927 18e6 eb6a 2a2a
0000040   \   \ 365   H 201 303 356   w   *   }   z   E 217 213 256 216
        5c5c 48f5 c381 77ee 7d2a 457a 8b8f 8eae
0000060   v 230 243 363 242  \v 243 255 275 342 342   M 246 263   . 263
        9876 f3a3 0ba2 ada3 e2bd 4de2 b3a6 b32e
0000100   T 345   " 263 251   4 253   ( 267 270   p 316 271 215 246   9
        e554 b322 34a9 28ab b8b7 ce70 8db9 39a6
0000120   X 030   u 036   G   f   b   ` 201 370 253   k   D   / 261   J
        1858 1e75 6647 6062 f881 6bab 2f44 4ab1
0000140   L 266 302 022 374   c 301 277   \   t   (   U 002 313   d 200
        b64c 12c2 63fc bfc1 745c 5528 cb02 8064
0000160 202 205 323   0 256   L 223 352 217 321 270 235   ~   g 265 323
        8582 30d3 4cae ea93 d18f 9db8 677e d3b5
0000200 334 260 214 314   & 265 215 220   T     001 244 261   e 245 366
        b0dc cc8c b526 908d 2054 a401 65b1 f6a5
0000220   ( 311   P 206 371 251 022   )   P 335 002 305 001 327 244 263
        c928 8650 a9f9 2912 dd50 c502 d701 b3a4
0000240 256   g   ] 002   3 020 352 027 262   R 215 345 336   : 267   C
        67ae 025d 1033 17ea 52b2 e58d 3ade 43b7
0000260 361   x 375   J 205  \v   .   v 245 266 316 345 267 227 271 235
        78f1 4afd 0b85 762e b6a5 e5ce 97b7 9db9
0000300 212 332   ) 005 235   r 226 373 275 276 231 232 305 220   & 302
        da8a 0529 729d fb96 bebd 9a99 90c5 c226
0000320 213 275 331 320   q 203 337   [   W   ^ 311   J   N   G   | 255
        bd8b d0d9 8371 5bdf 5e57 4ac9 474e ad7c
0000340 337   ^   ]   c 360 333   ]   X   } 036 245 217   )   6   6   #
        5edf 635d dbf0 585d 1e7d 8fa5 3629 2336
0000360   Y 351 243   $ 305 305   a 274   { 334 250 314   V 374   v 237
        e959 24a3 c5c5 bc61 dc7b cca8 fc56 9f76
0000400


```

---

### Post by Wayne_V on 2008-10-31
>>>  gzip: bomgar.gz: unexpected end of file

Hmmm ... maybe that is the whole problem.  Did you download abort early?   Can you confirm the size (and possibly checksum) of your .desktop file is correct?

---

### Post by Wayne_V on 2008-10-31
>>>  gzip: bomgar.gz: unexpected end of file

Hmmm ... maybe that is the whole problem.  Did your download abort early?   Can you confirm the size (and possibly checksum) of your .desktop file is correct?

---

### Post by flickerfly on 2008-10-31
I just downloaded it again, 3 times. It was 5492450 bytes each time.

On the bright side... It seems like in the last couple days they've updated the file. It now works out of the box and has this at the top of the file instead of what we've been working with.

```
l=. exec 2>>/dev/null
set -f
[Desktop Entry]




################################################################################
################################################################################
##
##  NOTE: If you are seeing this, then this file has not been invoked correctly.
##
##  Normally, you should simply save this file to a folder and then double-click
##  the file from the file system browser in your desktop environment.
##
##  Alternatively, you may execute this file from a terminal window using the
##  following command:
##
##     $ sh /path/to/this/file
##
################################################################################
################################################################################

```

I should note that I had to run this on the CLI. Just running by clicking on it still gives an error, but at least we have an alternative now.

---

