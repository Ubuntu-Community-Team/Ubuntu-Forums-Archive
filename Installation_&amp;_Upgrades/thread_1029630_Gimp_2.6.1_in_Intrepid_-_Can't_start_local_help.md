---
title: "Gimp 2.6.1 in Intrepid - Can't start local help"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by willy1946 on 2009-01-03
Hi guys. 
  I have a completely updated copy if Ubuntu Intrepid which works very well except for one minor prob. When I start the installed Gimp 2.6.1 and select Help->Help, it fails with a pop-up window showing
> **The Gimp help browser is not available**.

The GIMP help browser plug-in appears to be missing from your installation. You may instead use the web browser for reading the help pages
  While the web browser option does work, I would prefer to use the local help if possible. I searched the forums but could not find anything related to this other than a reference to a package called gimp-helpbrowser. I looked in Synaptic and no such package is listed. I then made the following query using aptitude from the terminal:
       > bill@Desktop:~$ aptitude search gimp | grep ^[iv]
i   gimp                            - The GNU Image Manipulation Program        
i   gimp-data                       - Data files for GIMP                       
v   gimp-help                       -                                           
i   gimp-help-common                - Data files for the GIMP documentation     
i   gimp-help-en                    - Documentation for the GIMP (English)      
v   gimp-helpbrowser                -                                           
v   gimp-python                     -                                           
i   libgimp2.0                      - Libraries for the GNU Image Manipulation P
  gimp-helpbrowser along with gimp-help and gimp-python are listed as virtual packages. None will install directly. 
An 'aptitude why-not' query against each results in the following:
> bill@Desktop:~$ aptitude why-not gimp-python
Segmentation fault
bill@Desktop:~$ aptitude why-not gimp-helpbrowser
i   gimp Conflicts gimp-helpbrowser
bill@Desktop:~$ aptitude why-not gimp-help
Segmentation fault
  A reinstall of Gimp failed to correct the problem. 
  Has anyone out there had the same prob and managed to fix it??

---

### Post by tigon5 on 2009-01-19
i have same issue, my gimp version is 2.6.1 on intrepid.

I did find an apparent solution which was to go to 'Edit>Preferences>Help System'   and to change 'Help Browser' to 'GIMP Help Browser'.  But, this is possibly outdated as the post referred to the dapper version of ubuntu, and it did not work for me.   

Just to confirm, I do have gimp-help-en installed, and can access this through the web browser as in the post above.

---

### Post by tvtech on 2009-06-10
I concur this is a problem, has anyone filed a big report yet? 

same problem as other two.  

I have NEVER had an install of Gimp that worked properly EVER.  from ubuntu 5.04 to 9.04.  This product should not be included if it's not going to install in a manner which the average BOOB  can figure out how to use it by hitting the help button.  

HOW CAN I RECOMMEND LINUX TO MY GRANDMOTHER WHEN IT DOESN'T DO BASIC THINGS WINDOWS DOES THAT MAKE MY LIFE EASY.   

I know I know Linux/BSD isn't windows.  However, it has to compete with them so guess what! Make Linux easier or be relegated to the sidelines forever. That's the choice. Seriously if APPLE can make BSD easy, the rest of the communities can too. Help files need to be standardized and searchable per application.   html help is useless to the average user, it's confusing and not context searchable. .CHM help files in windows are a GOD SEND best idea EVER easy to use and transport and easy to maintain and create.  

okay I've said my piece let me know if anyone files a bug for this.

---

### Post by krivine on 2009-09-29
I found this too, using Jaunty and Gimp 2.6.6. This worked for me. In Gimp:

[LIST=1]
[*]Click **Edit->Preferences->Help System**
[*]Set **User manual** to 'Use a locally installed copy'
[*]Set **Help browser to use** to 'Web browser'
[*]Set the** Web browser to use** field appropriately. Mine is 'firefox %s'
[/LIST]

---

### Post by tvtech on 2009-09-30
okay, we know that method works, you can also download the .html help file off gimps website... etc... etc... etc... still it's not searchable it's not a .chm and because of that it's not very useful!  I still feel the one thing that would make linux ultimately more usable is if the non developers would create sdk's for their products and the help systems were standardized!

man pages are typically useless and are written in ... sub English, and most times don't accurately or adequately describe what each switch does and many times don't even describe all available switches, or how to use them. Help files, when there is one, can be anything from some random .pdf to an .html to a who knows what!  Some are context searchable, most aren't.  Everyone in the commercial Linux community needs to get their head wrapped around the idea; that adoption will only happen if the product makes peoples lives easier.  Sorry to say but even with the headaches that MS has, it makes life easier because A. It works as advertised and within those advertised limits. and B. it has functional help files with almost every application that are designed built and standardized around the .chm format. Compiled help manuals or something very very similar is really the only way to go.  And yes I agree not all of them are perfect but have you tried reading Open offices manual it is a challenge at best.  where as Offices manual is pretty helpful and even shows examples and instead of a Forum they actually have a real sdk library.

Ok sorry for the more ranting but help files that work when you click help instead of getting some random error message would make Linux that much more usable.

---

