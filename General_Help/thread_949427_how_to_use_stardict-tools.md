---
title: "how to use stardict-tools?"
date: 2008-10-16
forum: General Help
---

### Post by ryu kun on 2008-10-16
Can you point me to a source where I can find information on how can I use stardict-tools package?

> "This package contains the dictionary conversion tools which can convert dictionaries of DICT, wquick, mova and pydict to stardict format"

I get this text when I use ```
apt-cache show stardict-tools
``` command but it is not enough.

---

### Post by shawnrgr on 2008-10-16
stardict is on sourceforge i believe... stardict.sourceforge.net

---

### Post by ryu kun on 2008-10-16
Yes but I could not find any info there.

---

### Post by lubart on 2012-07-25
May be it will interesting to some one even 4 years after this post :)

After instalation all stardict-tools you can found here:
[HTML]/usr/lib/stardict-tools/[/HTML]

and it is a list with describe of some tools:


**dictd2dic.sh(dictd2dic)**	converter from dictd format (you may need dictzip package for .dz)


**dsl2dict**	converter for Lingvo proprietary dictionaries (outdated by makedict)

**exc.sh(exc2i2e)**	converter of English irregular forms from WordNet-base package


**fest2dict**	converter from Festival (CMU) file of transcriptions

**i2e.sh(i2e2dict)**	converter for Spanish I2E (Inglés 2 Español) dictionaries


**myspell.sh(myspell2dic)**	converter that allows to see Spanish and Polish verb forms in correct grammar order (venir=>yo vengo, tu vienes, el viene... kocha&#263;=>ja kocham, ty kochasz, on kocha, my kochamy...)

**mova**		converter from MOVA format

**ooo.sh(ooo2dict)**		converter for OpenOffice (myspell) thesauri (synonyms) of	English, German and Italian. Sometimes they are easier	to grip than long GCIDE or WordNet description

**stardict2txt**	converter from StarDict to text format. Useful for mobile phones

**testutf8**	utility to test any dictionary's UTF-8 conformance (often	cause of weird symbols)

**ydp2dict**	converter for Polish Collins proprietary dictionaries (see also YDPDict project: [http://toxygen.net/ydpdict/](http://toxygen.net/ydpdict/))

**lingvosound2resdb**		converter from ABBYY Lingvo proprietary dictionary sound file into Stardict resource database

**resdatabase2dir**		converter from Stardict resource database file into resource directory. See dir2resdatabase for reverse conversion.

**dir2resdatabase**		converter from resource directory into Stardict resource database file. See resdatabase2dir for reverse conversion. stardict_verify	check StarDict dictionary for errors

**stardict-editor**	a GUI front-end combining a number of tools. They allows to convert StarDict dictionary <-> tab file, (Babylong file, BGL file) -> StarDict dictionary, verify dictionary.

**stardict_index**	print content of StarDict index file in human readable form

**stardict_bin2text**	convert normal binary StarDict dictionary into textual	xml-based dictionary. See doc/TextualDictionaryFileFormat

**stardict_text2bin**	convert textual xml-based dictionary into binary StarDict dictionary. See doc/TextualDictionaryFileFormat

**babylon**	convert from babylon source file format to StarDict dictionary see doc/HowToCreateDictionary for information about babylon source file format

---

### Post by wildmanne39 on 2012-07-25
Thanks for sharing. Thread Closed.

---

