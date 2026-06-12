---
title: "GEdit: Is there any way to Change the Encoding to Windows format?"
date: 2008-08-10
forum: General Help
---

### Post by OzzyFrank on 2008-08-10
Hi. You'd think by now I would have gotten it into my head that when I create a text document of more than one paragraph intended for Windows users I'd either:

1. Create it in Windows
2. Convert it with Notepad++ (which runs great in Wine) after creating it in Linux
or
3. Use something other than Gedit while in Ubuntu.

For those wondering why it would matter, it's because while text files created in Windows look fine in Ubuntu, people opening ones made in Ubuntu or other distros will (generally) just see one huge paragraph with rectangles interspersed in place of spaces between paragraphs. As you could imagine, it can end up looking nothing like how you designed it to be laid out.

Now, I've looked in the Preferences of Gedit and there is no option to set the default encoding, nor an option in the menus (like, for example, View > Encoding in Opera browser). I'm not too fussed about having to convert with Notepad++, it's just that because everything I type in Windows looks the same in Ubuntu, I forget to do that to those created in Ubuntu and destined for Windows users.

So I guess I'd like to know if there is a plugin for Nautilus that gives one the option of changing encoding [at least between ANSI and UTF-8], either manually or by setting a new default, or if there is a better Linux app for this. Cheers.

---

### Post by Forlornity on 2008-08-10
Although I'm not the most knowledgeable of individuals as regards the world of unix, I believe the problem is not to do with encoding so much as it is the format of line breaks used by unix and windows.
An easier workaround than using Notepad++ in Wine, certainly, is to run
```
sudo apt-get install tofrodos
```
Then run
```
unix2dos MYFILE
```

That said, I'm pretty certain there's a method for doing it within gedit.

- Forlornity

---

### Post by silkstone on 2008-08-10
Does it help if you change the default Gedit font (Edit > Preferences > Fonts and Colors) to a Windows font such as Times New Roman or Arial?

---

### Post by OzzyFrank on 2008-08-10
Hi guys. Thanks for the info on the command - even that might be a tad quicker, but for anyone wanting a great freeware Windows app that runs perfectly in Wine, do check out Notepad++ (you just go to the Format menu and tick another encoding).

And yes, I would have thought there is an option in Gedit, but I can't find it. That's why I asked if there is a plugin, which if there is I am sure plenty would know of.

As for the font, I don't think that would matter, as they are all true type fonts, it's just that the Windows ones aren't included in Ubuntu coz of copyright issues and whatnot. That's why you have to install a package to take care of that, or just drag all your fonts over like I do.

OK, just looked at **[COLOR="Purple"]Kate[/COLOR]**, being the default Kubuntu editor which I actually preferred at one point (I haven't gotten around to pimping my new 64-bit system yet and replacing my default apps). Sure enough, **Tools > Encoding** has a long list to choose from. And go to **Settings > Configure Kate > Open/Save** and you will see under **File Format** that you can change **Encoding** to whatever you want as the default, and **End of line** to either UNIX, DOS/Windows or Macintosh. I think this last option looks promising, since it appears you can have one encoding and the line break of another. But correct me if I am wrong, as I assume this means I can just leave the default encoding of UTF-8 and change the end of line format to DOS/Windows so paragraphs all look as they should when viewed in Windows Notepad.

---

### Post by OzzyFrank on 2008-08-10
Hey Forlornity: can you use unix2dos to batch process a folder of text files, ie **[COLOR="DarkRed"]unix2dox *.txt[/COLOR]**?

---

### Post by OzzyFrank on 2008-08-10
Hey, [COLOR="Red"]**unix2dos *.***[/COLOR] works great! It overwrites the originals, so if that isn't OK, make copies. Or you can use the backup switch like so **unix2dos -b *.*** to make backup copies of the original (same suffix with .bak extension).

Funny, couldn't get the help info for **unix2dos** so did **man unix2dos** and it gave me the manual page for **tofrodos**, where **unix2dos** isn't even mentioned. There it mentions the 2 commands being the opposite of each other, **fromdos** and **todos**.

[COLOR="#ff0000"]**QUESTIONS:**[/COLOR] If any of you guys know of an option to scan subfolders for files to convert, let me know. Also, does this command only work on text files? Or should I say, if I specify ***.*** will it try to convert the encoding of every file, no matter what it is? Should I specify ***.txt** when there are other filetypes, or is this not needed? But yeah, would like to know if there is an option to scan subfolders.

---

### Post by OzzyFrank on 2008-08-10
My mistake... **unix2dos** and its counterpart are mentioned in the manpage for **tofrodos**:

       **-d**     Convert from DOS to Unix. This forces the program to convert the file in a particular direction. By default, if  the  program  is named **fromdos** or **dos2unix**, it will assume that the input file is in a DOS format and convert it to a Unix format. If the  program is  named  **todos** or **unix2dos**, it will assume that the input file is in a Unix format and convert it to a DOS format. Using the -d option forces the program to convert from a DOS format to a Unix format regardless of how the program is named.  Likewise, using the -u option forces the program to convert from a Unix format to a DOS format regardless of the name of the program.

---

### Post by Andrew_P on 2009-11-24
> **OzzyFrank said:**
> And yes, I would have thought there is an option in Gedit, but I can't find it. That's why I asked if there is a plugin, which if there is I am sure plenty would know of.

If you check at the Gedit project plugins page ([http://live.gnome.org/Gedit/Plugins]("http://live.gnome.org/Gedit/Plugins")), it lists an **End of line** plugin that purportedly does just that, but, alas, the link ([http://myhpi.de/~wieland.hagen/endofline/]("http://myhpi.de/~wieland.hagen/endofline/")) is now dead.  I stepped up to the parent directory, but it only contains a couple of archive files that appear to be unrelated.  The date stamp on the archives is November 22, 2009, so it appears I may have missed getting the file by just a couple of days.  Unfortunately, the [Internet Archive]("http://www.archive.org/") doesn't have a copy, either because it was never submitted for archiving or the Wayback Machine never found a link to it.

My solution for now is to use [Metapad]("http://liquidninja.com/metapad/") in Windows, a free replacement for Notepad, that automatically detects EOL style and changes EOL characters between several different operating system styles with a couple of mouse clicks, although it's a bit of a pain having to send files back and forth between systems just to do this.  Seriously, detecting and changing EOL styles should be hard-coded into Gedit or supplied as a standard plugin with the distribution package, not a plugin that may or may not be available from a fickle third party.

*Update 2010-12-16: The source code for Metapad is now available from [https://github.com/alexd/metapad](https://github.com/alexd/metapad). Although the C code is reportedly in a dreadful state and not well commented, it might be useful to someone who is interested in noodling through it to see how the EOL problem was handled in Metapad and possibly writing a plug-in for Gedit.  Whatever Metapad's author, Alexander Davidson, did, it seems to be almost instantaneous, even on very large files.*

---

### Post by OzzyFrank on 2009-11-24
Yeah, I can use Notepad++ in Windows, and that's pretty advanced, and shows files as they should look without any mouse clicks. I use a command to convert all text files in a folder to Windows format, but is a pain to remember to do to those that need it. I know Kate can let you change encodings, but was hoping that since Gedit has so many users now, it might be on the cards.

---

### Post by rCXer on 2009-11-24
Like other's have said, KATE's one of the best options.  I stopped using gedit because of it's encoding limitations.

---

### Post by OzzyFrank on 2009-11-24
OK, Andrew_P, I only just noticed you mentioned sending files back and forth between systems. What's the reason for that? If they're all on the one machine, you can just copy between partitions/drives, so shouldn't be any need to send them.

Anyway, you should check out the **unix2dos** bit further below. I have a line in my bash_aliases (**alias 2dos='unix2dos *.txt'**) so all I need to do is open a terminal in a folder with text files I want to convert, and enter **2dos**, and all text files (with the .txt extension) are converted to DOS format. It's pretty easy as you can see.

Also, besides Kate, you could run Notepad++ for Windows (freeware) as it runs perfectly under Wine. I admit that since I can just convert a folder in one go with that command, and since for the most part I don't need to worry about encoding in Ubuntu, I'm not that fussed on this issue any more. Besides, even when using Kate for some Windows/ANSI text files I wanted to create, I'd sometimes forget to switch the encoding, so would have to convert after the fact anyway. So I recommend installing that command and making an alias for it like I did.

PS: While we're all admitting Gedit could do better by having encoding options, let's not forget the shortcomings of Notepad - like that it can't handle UTF-8, for example!

---

### Post by mmix on 2009-11-28
> **Andrew_P said:**
> 
My solution for now is to use [Metapad]("http://liquidninja.com/metapad/") in Windows, a free replacement for Notepad, that automatically detects EOL style and changes EOL characters between several different operating system styles with a couple of mouse clicks, although it's a bit of a pain having to send files back and forth between systems just to do this.  Seriously, detecting and changing EOL styles should be hard-coded into Gedit or supplied as a standard plugin with the distribution package, not a plugin that may or may not be available from a fickle third party.

Yeah, metapad is cool. 100x better than notepad!!!

---

### Post by Andrew_P on 2010-12-16
> **OzzyFrank said:**
> OK, Andrew_P, I only just noticed you mentioned sending files back and forth between systems. What's the reason for that? If they're all on the one machine, you can just copy between partitions/drives, so shouldn't be any need to send them.

I'm not running Ubuntu in a multiboot environment with Microsoft Windows on the same hard drive, let alone the same machine.  That way, if one system crashes, I don't lose all of them.  Windows systems have a habit of eating themselves eventually, even in the absence of malware.  Moreover, I just lost my Ubuntu 8.10 installation last week, forcing me to migrate to Ubuntu 10.04, because Canonical Ltd. have removed the software repositories for 8.10 last October and it is now *impossible* to get updates and applications for that system.  (Even though Microsoft ended support for Windows 98 in July 2006, I can *still* get patches for that system from their servers.  Compared to Microsoft, Canonical's support for its products sucks.)

---

### Post by OzzyFrank on 2010-12-16
I ended up doing a bunch of blog posts on this matter, with info on how to convert back and forth:

[http://ubuntugenius.wordpress.com/2010/10/26/creating-windows-text-files-in-ubuntu-how-to-save-as-ms-dos-end-of-line-in-gedit/](http://ubuntugenius.wordpress.com/2010/10/26/creating-windows-text-files-in-ubuntu-how-to-save-as-ms-dos-end-of-line-in-gedit/)

[http://ubuntugenius.wordpress.com/2010/10/26/creating-windows-text-files-in-ubuntu-how-to-convert-unix-end-of-line-to-ms-dos-format/](http://ubuntugenius.wordpress.com/2010/10/26/creating-windows-text-files-in-ubuntu-how-to-convert-unix-end-of-line-to-ms-dos-format/)

[http://ubuntugenius.wordpress.com/2010/10/26/how-to-convert-windowsdos-text-files-to-linuxunix-format/](http://ubuntugenius.wordpress.com/2010/10/26/how-to-convert-windowsdos-text-files-to-linuxunix-format/)

Hope these help others looking for similar info.

And as for Canonical's updates, well, yeah, it would suck for people wanting to hold onto versions 2 years or more old, but not too many people do that. At least they are quite up-front about the 18 months of updates for all non-LTS versions, and if you get the newsletter, you're even informed when each version has reached its end of life.

---

### Post by luigi_mb on 2010-12-16
When you are done editing, save the file using "Save as". You will see options to change "Character Encoding" and "Line Ending". 

/luigi

---

