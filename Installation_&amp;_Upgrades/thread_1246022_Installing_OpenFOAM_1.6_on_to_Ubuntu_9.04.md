---
title: "Installing OpenFOAM 1.6 on to Ubuntu 9.04"
date: 2009-08-21
forum: Installation &amp; Upgrades
---

### Post by wubi-lucy on 2009-08-21
Hi,

Just looking for some help with the installation of OpenFOAM 1.6.

When I get to the the part of the installation process to perform the foamInstallationTest, I get an error message : 

[I][B]FoamInstallationTest
Executing ./foamInstallationTest:


Checking basic setup...
-------------------------------------------------------------------------------

FATAL ERROR: OpenFOAM environment not configured.[/B][B]

    Please refer to the installation section of the README file:
    <OpenFOAM installation dir>/OpenFOAM-1.6/README
    to source the OpenFOAM environment.
[/B][/I]

I then go back to check on the previous step to configure these settings, the instructions go:

*The environment variable settings are contained in files in an etc/ directory in the OpenFOAM release. e.g. in $H**OME/OpenFOAM/OpenFOAM-1.6/etc*/

*Source       the etc/bashrc file by adding the following line to the end of your       $HOME/.bashrc file:                                                                                                                                                                   *
[LIST]
[*]*. $HOME/OpenFOAM/OpenFOAM-1.6/etc/bashrc*
[/LIST]
       *Then update the environment variables by sourcing the $HOME/.bashrc file       by typing in the terminal:            *

[LIST]
[*]*. $HOME/.bashrc*
[/LIST]

//

So I added ***. $HOME/OpenFOAM/OpenFOAM-1.6/etc/bashrc** *to the end of the text editor bashrc file the end of the code looks like this:[I]
[B]
.....
[/B][B]    cleanEnv=`$cleanProg "$LD_PRELOAD"` && LD_PRELOAD="$cleanEnv"
    export LD_PRELOAD

fi

# cleanup environment:
# ~~~~~~~~~~~~~~~~~~~~
unset cleanEnv cleanProg foamInstall foamOldDirs
unset _foamSource


. $HOME/OpenFOAM/OpenFOAM-1.6/etc/bashrc



# ---------------------------------------------------------------------------[/B][/I]

When I run $HOME/.bashrc in the terminal I get this error message:
[I][B]
lucy@lucy-laptop:~/OpenFOAM/OpenFOAM-1.6/bin$ $HOME/.bashrc
bash: /home/lucy/.bashrc: Permission denied
[/B][/I]
:confused:

Can anyone please help/advise me?

Thanks,

Lucy

---

### Post by pistacoppu on 2009-08-22
Maybe you have another version of openfoam installed?
In that case you have to create more aliases and use each one for the version of openfoam you want to use.
I'm not an expert, i'm just giving an idea
bye

---

