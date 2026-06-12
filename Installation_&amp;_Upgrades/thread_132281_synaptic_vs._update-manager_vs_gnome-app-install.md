---
title: "synaptic vs. update-manager vs gnome-app-install"
date: 2006-02-18
forum: Installation &amp; Upgrades
---

### Post by najevi on 2006-02-18
I have many questions relating to[LIST]
[*]**synaptic** 0.57.4ubuntu10
    *a.k.a.  System - Administration - [COLOR=Navy]Synaptic Package Manager[/COLOR]*
[*]**update-manager** 0.37.1+svn20050404.15[I]
a.k.a.  System - Administration - [COLOR=Navy]Update Manager[/COLOR][/I]
[*]**gnome-app-install** 0+20051005[I]
a.k.a.  System - Administration - [COLOR=Navy]Add Applications[/COLOR][/I][/LIST]that might warrant clarification in ubuntu documentation or at least here at the forum. A couple are really feature requests.
 
** 1)** Synaptic is listed as a dependency for update-manager and for gnome-app-install so I infer from this that the three apps are inter-related and should work harmoniously together (not necessarily integrate) - is that a reasonable assumption? Are there any caveats?

**1.1)** Neither update-manager nor gnome-app-install is listed under the dependencies for synaptic and yet the synaptic repository management window and most notably the Settings window (accessed via the Setting button below the list of repositories) *is very different after update-manager and gnome-app-install* have been installed.

I did not install them separately to pinpoint which introduced the changes discussed at item 3 below. In item 3 when I refer to update-manager you might read that as "update-manager and/or gnome-app-install"
 
** 2)** Synaptic refers to **History** files both in the Preferences and in the File menu. Maybe it was there all along but I suspect this also showed up *after* I installed update-manager - *is this the case?* If it was there all along then it has not been recording a history of the plethora of packages I have installed since installing ubuntu-breezy.
   
** 2.1)** When update-manager or gnome-app-install are used to retrieve and install packages, is this same History updated?
Where are those history files stored?
 [B]
 2.2)[/B] Could the documentation for **History **please describe how to not only *remove an app/package* but also *where to look for cleaning up user customizations for this app/package*? An example might be the *.asoundrc* file when a driver for a sound card is being removed. Is this feasible or too hard?
 
** 2.3)** Could a listing of installed packages be made available that is able to be sorted based on how OFTEN and how RECENTLY that package/app was used (preferably by user but aggregated would be a good first step)? The classic scenario is the spring cleaning day when it would be good to get rid of application bloat.

I did uncover the GNU Accounting utilities package - **acct** . After reviewing *man sa*, *man ac* and *man acct* I gained a little command line experience with sa and ca. That package of tools appears to be accounting at a process (micro-level) as opposed to the application (macro-level) that I am looking for.
Although it never reported meaningful data, the *Add/Remove Programs* applet from the Windows world, is perhaps the closest thing to illustrate what I am after. 

 
** 3)** Synaptic repository Settings options before and after install of update-manager are different. Most notable is the unexpected appearance of a **default 500MB ceiling** on the size of the **/var/cache/apt/archives**

* When I refer to update-manager here you might read that as  "update-manager and/or gnome-app-install"*
 
The user is not informed of a cache disk quota or ceiling being in place *before *update-manager is installed. Therefore the installation of update-manager should not cause a default ceiling to be put in place.
Same can be said for the "package max age" threshold. **Am I alone in finding this default setting to be undesirable?**
 
** Rationale:** many new-to-linux types will use Synaptic or some-such to download >500MB of .deb packages within 24 hours of installing ubuntu-breezy. What's more we (newbies) are perhaps the most likely to be in a situation where a *clean install of ubuntu is desirable within one or two weeks*. 
It is then desirable to have a backed up archive of the **/var/cache/apt** directory tree on a local fileserver or a separate partition. This is to avoid duplicating the download of data. *Downloaded data is metered by most Australian ISP's, some even meter uploaded data.* 
 
** 3.1)** **Repository Settings:**  common to Synaptic, Update Manager and Add Applications 
 "Delete old packages in the package cache - Max Age=" 
This is *really *bothersome under the scenario described above. When I inspect either *Modified Date* or *Accessed Date* for the files in **/var/cache/apt/archives** I see very few *.deb* files that actually reflect the last date of Access - and yet even when this date is much older than 30days they have not been purged (*thank goodness!*)
***  So, what date is being used for this purge rule?***
 
** 4)** Synaptic - **how many apps are too many in one batch?**
 I read with keen interest the ubuntu-breezy forum discussions about Automatix - the "*automated is best*" versus "*manual is best*" arguments gave me some perspective. For my situation I realize that I needed both. I first needed an *open-the-flood-gates Automated* approach to get me started and to discover/sample *"what is available"*; only after this (and a clean install of ubuntu) does *a piece-meal Manual* approach seem desirable to do it all over with a *"less is more"* philosophy and an eye to such considerations as: purely license-free, ubuntu-supported, security or some other personal preference.
 [I]
To digress just a little:[/I] I have had bad experiences with **both** Synaptic **and** Automatix when I, albeit, frivolously checked every thing that looked "cool" to try out. The system either ran out of disk space, stopped responding, became unstable or some package that did not completely install would hide like a time-bomb to bite me later - the later version (v1.5?) of Firefox (and/or an associated plugin) was such a time bomb in my case. So I learned the hard way that *less is more* when it comes to installing packages.

Maybe some advice to that effect in the online Help (eg. for Synaptic, but equally relevant to gnome-app-install) would be a good idea. **Does anyone have an experience-based guide line?**
 
** 4.1)** The Synaptic Terminal window that shows a detailed log of apt-get and dpkg operations: -* that log text is not able to be copied.*
It's a great window for positive feedback when you get the "*All packages successfully installed, you may close...*" message. However, when you have an error to track down or a package to retry it would be a blessing to be able to select and copy the text of that terminal output to a text editor. Screenshots just don't cut it in this situation. **Has anyone figured out how to copy that text into a paste buffer?**

**5)** Synaptic - **is there a** *make -n* **style of output?**
What I imagine is capturing the shell commands used by Synaptic into a text file and then building a shell script to automate the task of installing the same set of packages on each of several machines (that may not necessarily have the same hardware configuration). 
This type of enumerate but don't execute output may help the newbie to get over the fear of the command line interface and using apt-get, dpkg and pgp.


enjoy!

---

