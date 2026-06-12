---
title: "Abiword in french"
date: 2004-12-23
forum: General Help
---

### Post by Denis the P. on 2004-12-23
I have installed Ubuntu in french. I installed the french locales for OpenOffice and Firefox and it is working OK. How can I get Abiword to work in french?

Thank you all!

---

### Post by feneks on 2004-12-25
use command
**find AbiWord.Profile**
or
**locate AbiWord.Profile**

There should be at least a hidden directory in your home directory called
*.AbiSuite*
within you will  find the file *AbiWord.Profile*

**gedit /home/.AbiSuite/AbiWord.Profile**

chanche all edits **_builtin_**  to **_custom_**
change all edits *EnEN* withinin MenuLabelSet="EnEN", StringSet="EnEN" and ToolbarLabelSet="EnEN" to "FrFR"

I read this at the german online guidebook for Debian
[http://www.openoffice.de/linux/buch/text.html](http://www.openoffice.de/linux/buch/text.html)

---

### Post by Denis the P. on 2004-12-27
...did not work... here is the file:

<AbiPreferences app="AbiWord" ver="1.0">

	<Select
	    scheme="_custom_"
	    autosaveprefs="1"
	    useenvlocale="1"
	/>

	<!-- The following scheme, _builtin_, contains the built-in application
	**** defaults and adjusted by the installation system defaults.  This scheme
	**** is only written here as a reference.  Any schemes following this one
	**** only list values that deviate from the built-in values.
	**** Items values must observe XML encoding for double quote (&quot;),
	**** ampersand (&amp;), and angle brackets (&lt; and &gt;).
	-->

	<Scheme
		name="_builtin_"
		AutoSaveFile="0"
		AutoSaveFileExt=".bak~"
		ColorRevision2="ab1477"
		ColorSquiggle="ff0000"
		OptionsTabNumber="0"
		StringSetDirectory="strings"
		StatusBarVisible="1"
		layoutMode="1"
		ColorShowPara="7f7f7f"
		ColorRevision3="ff9708"
		ColorRevision10="ff0000"
		/>

	<Scheme
		name="_custom_"
		MenuLabelSet="FrFR"
		OptionsTabNumber="3"
		ShowSplash="0"
		StringSet="FrFR"
		ZoomPercentage="117"
		ToolbarLabelSet="FrFR"
		/>

	<Recent
		max="4"
		/>

	<Geometry
		width="800"
		height="600"
		posx="34"
		posy="139"
		flags="2"
		/>

</AbiPreferences>

...when I change the _builtin_ part to custom  it keeps reverting back to _builtin_ after running AbiWord once (and it is not in french even for the first run)

---

### Post by feneks on 2004-12-27
Merde 

Found a FAQ-Site for Abiword. 
[http://www.abisource.com/twiki/bin/view/Abiword/AbiWordFAQ#Language_and_Internationalizatio](http://www.abisource.com/twiki/bin/view/Abiword/AbiWordFAQ#Language_and_Internationalizatio)

by the way:
found a french ubuntuforum [http://forum.ubuntu-fr.org/](http://forum.ubuntu-fr.org/) 
There aren't many postings and users yet. But somebody could know the solution there.

[http://www.andesi.org/forum/](http://www.andesi.org/forum/) is a french forum for debian which allocates an Ubuntu-section.

---

### Post by Denis the P. on 2004-12-27
Made it!...by trial and error...

Had to replace the FrFR by fr-FR everywhere. Hope it might help others and thanks to Feneks for guiding me.

Happy New Year to All!!

---

### Post by DjRomeo224620 on 2007-05-15
> **Denis the P. said:**
> Made it!...by trial and error...

Had to replace the FrFR by fr-FR everywhere. Hope it might help others and thanks to Feneks for guiding me.

Happy New Year to All!!


[Cash Advance Debt Consolidation pollution food science Credit Cards](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/incest-porn.html)

---

