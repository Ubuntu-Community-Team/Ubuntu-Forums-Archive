---
title: "Radeon HD 7700 not working properly on Ubuntu 12.10?"
date: 2012-11-29
forum: Hardware
---

### Post by deadlylady on 2012-11-29
I am a newbie at ubuntu, so please excuse me for obvious/retarded mistakes.

This is my original problem:
>                                                     Not software rendered:    no
Unity 3D supported:       no                      Along with countless problem-windows popping up now and then. 

So far I've installed Ati binary driver as described in [COLOR=Red]*[this]("http://askubuntu.com/questions/162831/ubuntu-12-04-radeon-hd-6670-help")*[/COLOR] page, but that only messed things up worse with all the window decoration suddenly not working with compiz.

I was guided to [COLOR=Blue]*[this]("http://ubuntuforums.org/showthread.php?t=2085133&highlight=Radeon+HD+7700")*[/COLOR] thread from another thread I started and thought I found the solution in a [COLOR=Blue]*[new driver]("http://support.amd.com/us/kbarticles/Pages/AMDCatalyst1211betadriver.aspx")*[/COLOR] for my card. 

However the installer won't let me install:
> One or more tools required for installation cannot be found on the system.
Install the required tools before installing the fglrx driver. Optionally, run the installer with --force option to install without the tools.
Forcing install will disable AMD hardware acceleration and may make your system unstable. Not recommended.
See /usr/share/ati/fglrx-install.log for more details.The install-log dosen't exist in the given path during the installation-process and afterwards the entire folder disappears. Nor does a search for the logfile render any hits, hence I do not know what "required tools" I should be downloading?
 
I looked up [COLOR=Blue]*[force-installing ]("http://askubuntu.com/questions/104225/how-do-i-force-install-a-run")*[/COLOR]and tried the advise offered but they both resulted in previous result(above error-message). Is it even advisable to force-install and if so how do I do it seeing that the "chmod a+x *.run" and "sudo ./*.run" commands aren't doing it?

Any other ideas what I should do to get my graphic card in sync with Ubuntu?

---

