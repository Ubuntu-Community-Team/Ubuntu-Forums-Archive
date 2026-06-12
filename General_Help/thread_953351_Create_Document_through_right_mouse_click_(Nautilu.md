---
title: "Create Document through right mouse click (Nautilus Templates)"
date: 2008-10-20
forum: General Help
---

### Post by I wanted to leave on 2008-10-20
I've searched these threads for a solution but could find no answer to this question...
When I right mouse click and select 'Create Document' the only option available is 'Empty File'. I have seen some suggestions to add blank doc's to the hidden Templates folder in /home which are then available via right mouse click. However doing this drops only drops a file of that type on the desktop, and that's not what I want. I even tried dropping a copy of oo writer from the applications menu in the Templates folder, but it just drops a file on the desktop also, but if left on the desktop, it launches the app!!! :confused: 
What I want to do is be able to click on the file type and have the app open. I used to do this using shortcuts to templates in windows, where you could not save to the template. This must be possible in Ubuntu surely... 
Can anyone shed any light?

---

### Post by rudihawk on 2008-10-20
I know you can enable all of this using a program called "ubuntu tweak" (its in the repo's i think) or you can probably get it from "getdeb."

Then once you have the program, go to the "Personal Tab" and then you'll be able to choose what you want at the "Templates Tab"

Hope this helps.

---

### Post by scorp123 on 2008-10-20
> **bra10n said:**
>  When I right mouse click and select 'Create Document' the only option available is 'Empty File'. Well, there have already been many threads where this was discussed, e.g. here:
[http://ubuntuforums.org/showthread.php?t=84095](http://ubuntuforums.org/showthread.php?t=84095)

Another nice way to get templates is to use "Ubuntu-Tweak" .... Maybe if you used Windows before you are familiar with the set of tools commonly known as "PowerToys"? There was one amongst those that I consider to be really really useful: "TweakUI" ... Well, Ubuntu-Tweak offers similar functions (and a lot more on top!). So here is how to get it:

1. Open a terminal (Applications > Accessories > Terminal)

2. Type this command:
```
gksudo gedit /etc/apt/sources.list.d/ubuntu-tweak.list
``` ... When it asks for a password: That's your own password (and I assume here that you are in the "admin" group and therefore allowed to execute administrative commands via "sudo")

3. A text editor should have opened, displaying nothing. So let's write the file. Copy and paste this .... :
```
# UbuntuTweak
deb http://ppa.launchpad.net/tualatrix/ubuntu hardy main
deb-src http://ppa.launchpad.net/tualatrix/ubuntu hardy main
```

4. Save + close

5. Refresh your package list:
```
sudo apt-get update
```

6. Make sure all your patches are up to date:
```
sudo apt-get dist-upgrade
```

7. Finally, install "ubuntu-tweak":
```
sudo apt-get install ubuntu-tweak
``` ... Here the package manager will complain that "ubuntu-tweak" is an "unsigned package" and it will ask you if you really want to continue installing it ... Hit "Y" for yes. It should proceed to download and install the program.

8. Once the program is installed you will find it here:
Applications > System Tools > Ubuntu Tweak

You will find the "Templates" stuff under the "Personal" menu entry. Using this should be easy and straightforward. 

One piece of advice: Just don't touch any of the other options inside "Ubuntu Tweak" if you are not sure what they do, OK?

Here is a screenshot of Ubuntu Tweak in action, managing my templates:

[IMG]http://s121.photobucket.com/albums/o217/scorp123_2006/Screenshots/th_Ubuntu-Tweak_managing_Templates.jpg[/IMG]

Full size image is [here]("http://i121.photobucket.com/albums/o217/scorp123_2006/Screenshots/Ubuntu-Tweak_managing_Templates.jpg")

---

### Post by I wanted to leave on 2008-10-20
Thank you for the replies...
I tried U-T but it does the same thing, just drops a file on the desktop.
I really like to be able to launch the app instead
cheers anyway

---

### Post by scorp123 on 2008-10-20
> **bra10n said:**
>  I tried U-T but it does the same thing, just drops a file on the desktop.  Well then, there is a difference between a file template and a launcher action ;)

You may want to look into "Nautilus action" then ... this allows to modify the "right-click" menu. Ubuntu-Tweak offers such options too.

---

### Post by I wanted to leave on 2008-10-20
Thank you again for your help but I'm giving up on this one. 
Scouring other posts re nautilus-actions, the consensus appears that it also will not do this.
 
Can't believe it's been this much trouble just trying to get what is in windows terminology, 'a shortcut to a file template copied to a menu folder'

Thanks all once again

---

### Post by Tomatz on 2008-10-20
jhygjhgb

---

### Post by scorp123 on 2008-10-20
> **bra10n said:**
>  Can't believe it's been this much trouble just trying to get what is in windows terminology, 'a shortcut to a file template copied to a menu folder' Linux is not Windows. Perhaps it would help if you could describe in more details (and maybe with screenshots?) what you mean? I really don't get the meaning of "a shortcut to a file template copied to a menu folder" ....

But then again I haven't seen Windows on any of my PC's since 1996. I see Windows XP and Windows 2003 here and there at work, but I don't remember seeing anyone using something like the feature you describe. Could you explain please?

---

### Post by random turnip on 2008-10-20
You need to understand that Ubuntu and windows are not the same thing.

It runs differently from Window's thats why people use it, so you can't expect every short cut and tool to be in the same place else there would be no use in have Linux at all.

---

### Post by I wanted to leave on 2008-10-20
So glad Ubuntu's not windows, believe me :)

The only reason I mention templates is for the fact you don't inadvertently 'save' data to them. It just creates a doc file saved to a location of your choice. But never mind that part of it. 

What I want to do is simply select say an oo word link or shortcut in the right-click menu and have the oo word application open

Hope that's a bit clearer...

thanks again

---

### Post by I wanted to leave on 2008-10-20
Or if I put it a different way by means of a question...

If I create a word launcher on the desktop then move it to the 'Create Document' menu, why does the launcher now NOT open, but simply drop a word file on the desk when I select it?

---

### Post by scorp123 on 2008-10-20
> **bra10n said:**
> why does the launcher now NOT open, but simply drop a word file on the desk when I select it? Well, you could easily create a launch action for Nautilus, e.g. "Open this in OOo-Writer" as described previously (or rather: hinted at previously ...). And even if it just creates an empty document: click on it and OOo-Writer should have opened too.

---

### Post by I wanted to leave on 2008-10-20
Just so I'm being understood....

If I click on the desk icon in the first screen it opens the app

If I move it to the menu, see second screen, I click it and it drops a file on the desk. Why does it no longer open?

---

### Post by lowlymarine on 2008-10-20
Let me see if I understand what you're asking for...

Currently, the behavior of going to a folder in Nautilus (or simply being on the desktop), right-clicking, and selecting "Create Somefiletype" is for a file of said type to be created in the working directory.  What you *want* is for Nautilus to instead open the associated application for Somefiletype?  I'm not sure there's a way to do that, though it begs the question of why you couldn't simply add OpenOffice or what have you to the quick launch...

---

### Post by scorp123 on 2008-10-20
> **bra10n said:**
> ... screenshots ...  Hey, nice theme :D  Yes, I am OT ... but what theme is that? :D

---

### Post by redscorpion99 on 2008-10-20
hi try this download easystroke make your gesture in argument field type "ooffice -writer" u can use this 4 any program 1 more thing the program has 2 be running

---

### Post by dmizer on 2008-10-20
I can duplicate your problem.

Are you using NFS?

---

### Post by jerome1232 on 2008-10-20
I think I get it finally, you want it to create the file AND launch Open Office? Not just create the file right?

---

### Post by talkingwires on 2008-10-20
The solutions people have been posting are very convoluted and require installing third-party software. The proper solution is much easier, and cleaner, too.[LIST=1]
[*]Go to your home directory.
[*]Create a new folder called "Templates" (no quotes).
[*]Now, for each type of document you'd like to appear in the right-click menu, do the following: open the the respective application, create a new document, save the document to the ~/Templates folder.[/LIST]By doing it this way, you can also create customized defaults. Say you always want to create a new Open Office document with a certain typeface for the title and another for the body. Whip it up, and save it in the  ~/Templates folder. Each new document will be started from this template.

---

### Post by GeordieJedi on 2008-10-20
Just wanted to say a very quick thank you to scorp123.

I followed your instructions, to install Ubuntu tweak
and they worked flawlessly.

Cheers.

---

### Post by mc4100 on 2008-10-20
> **bra10n said:**
> What I want to do is be able to click on the file type and have the app open.
It's hard to understand what you **really** want, but this is how I interpret it:

When I right click a *text file*, for example, I see, "Open With..." and then applications for text-editing. Like, "Open with Text Editor", "Open with OpenOffice Writer", etc,. 
This is good for selectively opening certain file types with different applications. If it's an image file, then the context menu will show apps related to images. 
Combine this with "Create Document" templates: 
[list][*]Right-click the desktop
[*]Go to the "Create Document" entry
[*]Create, say, a text file
[*]Now right-click **that** file and you have a choice of which application to open it with.[/list]

  If you want to change the default app, right click the file, then "Properties", and change the program in the "Open With" tab.
Does this help?

Edit: OH, I just reread your post. Are you saying you want a shortcut to **OpenOffice.org Writer** in the right-click menu, that will be called, not "Writer", but have the name of the *file type* which you want to open in Writer?

---

### Post by dmizer on 2008-10-20
> **talkingwires said:**
> The solutions people have been posting are very convoluted and require installing third-party software. The proper solution is much easier, and cleaner, too.[LIST=1]
[*]Go to your home directory.
[*]Create a new folder called "Templates" (no quotes).
[*]Now, for each type of document you'd like to appear in the right-click menu, do the following: open the the respective application, create a new document, save the document to the ~/Templates folder.[/LIST]By doing it this way, you can also create customized defaults. Say you always want to create a new Open Office document with a certain typeface for the title and another for the body. Whip it up, and save it in the  ~/Templates folder. Each new document will be started from this template.
This is what both I and the OP have done.

A couple of things:
1) ~/Templates already exists by default, so all you have to do is create a blank template file and put it there.
2) For some people (myself and the OP included), this does not open OOo with a blank document like it should. All it does is place an empty document on the desktop.

I spent an hour or so looking through bug reports and trying different things to make this work, and I have not made any progress.

Edit:
Moved to desktop effects and edited title to reflect the problem more closely.

---

### Post by Steve H on 2008-10-25
> **scorp123 said:**
> Well, there have already been many threads where this was discussed, e.g. here:
[http://ubuntuforums.org/showthread.php?t=84095](http://ubuntuforums.org/showthread.php?t=84095)

Sorted, so simple! Champion!!

---

### Post by I wanted to leave on 2008-10-27
> **dmizer said:**
> This is what both I and the OP have done.

A couple of things:
1) ~/Templates already exists by default, so all you have to do is create a blank template file and put it there.
**2) For some people (myself and the OP included), this does not open OOo with a blank document like it should. All it does is place an empty document on the desktop.**

I spent an hour or so looking through bug reports and trying different things to make this work, and I have not made any progress.

Edit:
Moved to desktop effects and edited title to reflect the problem more closely.

Thank you dmizer for the title tidy up :)

I have highlighted in bold the key point of your post above...

No matter what I tried I couldn't get the application to open directly from the menu item, regardless of what I try

Thank you to all who have posted here though :)

---

### Post by dmizer on 2008-10-27
bra10n, I still cannot find any more information on how to fix this, nor have I been able to resolve it on my own.

I suggest that you file a bug report: [http://kmandla.wordpress.com/2007/12/20/howto-file-a-bug-report-on-launchpad/](http://kmandla.wordpress.com/2007/12/20/howto-file-a-bug-report-on-launchpad/)

Once you do, please link to it here, and I will watch it.

Thank you.

---

### Post by I wanted to leave on 2008-10-27
I'm not sure that it is a bug though...
Is the app meant to open like this? I know I could make it do this in windows but I'm not sure about Ubuntu

A bug report though if you say so :)

Bug filed here

[https://bugs.launchpad.net/ubuntu/+bug/290126](https://bugs.launchpad.net/ubuntu/+bug/290126)

---

### Post by dmizer on 2008-10-27
Yes, this is a bug. The feature should work as you describe, but it does not.

I've subscribed to the bug and added comments.

---

### Post by I wanted to leave on 2008-12-18
Not wanting to give up on this I have filed the following:
 
[http://bugzilla.gnome.org/show_bug.cgi?id=565050](http://bugzilla.gnome.org/show_bug.cgi?id=565050) 

dmizer thanks for your support with this. Posted FYI only...

---

### Post by kadm on 2010-01-08
Well I've look at about ten threads regarding the same topic, I created my Templates folder and drop some empty documents for different file types, but the entries never appeared on the right-click menu.

After further searching, I found I was missing something on my ~/.config/user-dirs.dirs file:

On Karmic (dunno about others) the directive XDG_TEMPLATES_DIR defaults to "$HOME/". Should be:

XDG_TEMPLATES_DIR="$HOME/Templates"

Hope it helps others who could get confused about why the solution proposed here are not working for them. Seen at [http://www.len.ro/2009/03/nautilus-templates/](http://www.len.ro/2009/03/nautilus-templates/)

---

### Post by QwUo173Hy on 2010-05-05
It's working on the default Lucid install. Creating a new document from a template stored in the Templates folder. (I doesn't launch an application as some think it should, but I think this behaviour is correct. The menu entry says 'create document' and not 'create document and launch an application')

---

### Post by bra|10n on 2010-05-17
> **jarlath said:**
> It's working on the default Lucid install. Creating a new document from a template stored in the Templates folder. ([COLOR=Red]It doesn't launch an application as some think it should, but I think this behaviour is correct.[/COLOR] The menu entry says 'create document' and not 'create document and launch an application')

Correct. What I originally proposed is not default behaviour.

Link to current discussion:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/372132](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/372132)

If you read through the bug comments, you can see this discussion going around in circles. 
In my humble opinion, this is because the basis for any enhancement in this regard is too narrowly focused. 
What do I mean by this? Well I ask you what benefit is a create document link in the menu if it just throws a file on the desktop and the file isn't open? I might just as well use a launcher! At least then I can save the file where I wish first up without having to go back and 'clean up' blank files from the desktop.
However sadly, the discussion seems to be pointing at current default behaviour, debating only who, how and what default templates to include.

I do realise that many people seem to be confused by this, and perhaps by me also ;)
However, I just ask that you think about it from this point; What are you trying to achieve by using this feature? How efficient is the current method?

I posted a 'wish-list' bug here at Gnome re this also:

Previous discussion and history here: [https://bugzilla.gnome.org/show_bug.cgi?id=131793](https://bugzilla.gnome.org/show_bug.cgi?id=131793)

My simple request here: [https://bugzilla.gnome.org/show_bug.cgi?id=565050](https://bugzilla.gnome.org/show_bug.cgi?id=565050)

---

### Post by QwUo173Hy on 2010-05-17
Personally, my templates have a bit of detail in them and I prefer to plonk them in the relevant folder via the right click. Then I  rename it, and then launch the app. It seems a bit odd to me that I could launch an application through the right click.

I can see why discussions around this would go around in circles. Both solutions seem a little odd to me now!

---

