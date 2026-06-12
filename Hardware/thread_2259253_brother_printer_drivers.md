---
title: "brother printer drivers"
date: 2015-01-03
forum: Hardware
---

### Post by jimbo10 on 2015-01-03
am looking to get Brother printer drivers for a DCP-J515W printer....

went to their web pg but it was abt as clear as 'mud'......  :(

DCP-J515W is not supported in printer installs under "system settings"......

have dwn/ld "synaptic" but don't know what "CUPS" and "lpr" refer to......?  :confused:

(hmm.....will hafta get hold of one of those UBUNTU linux manuals but don't like the idea of paying $40-odd for it....might see if its available on a 'torrent' site, eh?)


thnx!

---

### Post by Bucky Ball on 2015-01-03
Okay, here ya go:

1/ Go [HERE]("http://support.brother.com/g/b/downloadlist.aspx?c=au&lang=en&prod=dcpj515w_eu_as&os=128") and download the Driver Installer Tool, first one on the list;
2/ Double click the downloaded .deb file and install (Software Centre will probably open to install it);
3/ Once installed, open 'Printing' and 'Add Printer';

You should be able to follow your nose from there and the driver should be available in the list of drivers when you get there.

Good luck. Any roadblocks, just ask. ;)

[THIS]("http://support.brother.com/g/b/downloadend.aspx?c=au&lang=en&prod=dcpj515w_eu_as&os=128&dlid=dlf006893_000&flang=4&type3=625") link takes you directly to the .deb download. You just need to agree to the EULA and the download should start.

* Just noticed something from the link above in 'Install notes'. You can only install the Install Tool via the terminal. That is fine. Extract the file that downloads and you should find a 'Read me' file in there. Have a read of that and you should get the instructions for installing from command line. Anything you don't understand, post here.

---

### Post by jimbo10 on 2015-01-04
nah...didn't work....

after "unzipping"..... and "tapping in" the following cmnd......  [I][B]bash linux-brprinter-installer-*.*.*-* Brother machine name
[/B][/I]
i got: "no such command or file name"    :(

actually......wht's "up" with the "bash"?

is that to change shells to the 'Bourne Again' shell?

(yr already in the 'Bourne' shell @ the command prompt ain't ya?  :confused:   )


cheers!

---

### Post by kurt18947 on 2015-01-04
May I butt in for a moment?  This is my default method for installing Brother printers and scanners.  I've had very good luck with it.  Please excuse me if I'm overly simplistic.  This needs to be run from an account with SUDO/administrative privileges. Once you've downloaded and extracted the installer file open a terminal, navigate to the folder to which the files were extracted  and I run the command "ls".  You should see "linux-brprinter-installer-2.0.0-1" listed. This is just to check that I'm in the correct folder.  Type the following command:

```
sudo bash linux-brprinter-installer-2.0.0-1 DCP-J515W
```

The script should start, you'll be asked to agree to a couple licenses and the printer will install.  The scanner install script will then start if you agree to the licenses.   If you don't wish to install the scanner, decline the license agreement and the script will terminate. The scanner install may require a couple tweaks but we can cross that bridge when and if necessary.

---

### Post by jimbo10 on 2015-01-04
> **kurt18947 said:**
> May I butt in for a moment?  This is my default method for installing Brother printers and scanners.  I've had very good luck with it.  Please excuse me if I'm overly simplistic.  This needs to be run from an account with SUDO/administrative privileges. Once you've downloaded and extracted the installer file open a terminal, navigate to the folder to which the files were extracted  and I run the command "ls".  You should see "linux-brprinter-installer-2.0.0-1" listed. This is just to check that I'm in the correct folder.  Type the following command:

```
sudo bash linux-brprinter-installer-2.0.0-1 DCP-J515W
```

The script should start, you'll be asked to agree to a couple licenses and the printer will install.  The scanner install script will then start if you agree to the licenses.   If you don't wish to install the scanner, decline the license agreement and the script will terminate. The scanner install may require a couple tweaks but we can cross that bridge when and if necessary.

nah....won't do it....keeps coming up with the same lousy msg......[I]no such file or directory

[/I]&#8203;hvn't the "foggiest" wht i'm doing wrong here.......  :frown:

('dltd' the original .gz from dwn/lds dir'.....re-dwn/ld.....now.....i can't even "unzip" it  :( ...............UN-believable!!.......uh.....re: executing that command....should the file be mv to the usr/local/bin dir' ? .......ain't that where you put all executable scripts and that, eh?!?)

ta! any-way(s), eh?!?

---

### Post by Bucky Ball on 2015-01-04
Ok, in that case ...

Download the LPR and CUPS Wrapper .deb files from [here]("http://support.brother.com/g/b/downloadlist.aspx?c=au&lang=en&prod=dcpj515w_eu_as&os=128"). 

Once downloaded, double click them and Software Centre should pop up and ask you to install. Do it.

Then follow the instructions I gave previously. Go to 'Printing' and 'Add Printer'. You should find the driver there when you get to that bit, but you need to LOOK for it when that bit comes up. 

Good luckster. ;)

---

### Post by jimbo10 on 2015-01-04
> **Bucky Ball said:**
> Ok, in that case ...

Download the LPR and CUPS Wrapper .deb files from [here]("http://support.brother.com/g/b/downloadlist.aspx?c=au&lang=en&prod=dcpj515w_eu_as&os=128"). 

Once downloaded, double click them and Software Centre should pop up and ask you to install. Do it.

Then follow the instructions I gave previously. Go to 'Printing' and 'Add Printer'. You should find the driver there when you get to that bit, but you need to LOOK for it when that bit comes up. 

Good luckster. ;)


holy snappin' [COLOR=#ff0000]***tad-poles  ***[/COLOR]):P
it actually worked!
(done it all from the cmmnd line/Term' win, eh?)

m8.....i owe you a beer, eh?   

cheers!

---

### Post by Bucky Ball on 2015-01-04
ROCK ON! jimbo. Nice work. I like it when a plan comes together. ;)

See you in Ballas for that beer.

PS: You're becoming an expert! Nice terminal work.

* Addendum: Those .deb files you downloaded, couldn't you just double click them and they would install via Software Centre?

---

