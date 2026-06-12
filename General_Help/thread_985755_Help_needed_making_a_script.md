---
title: "Help needed making a script"
date: 2008-11-17
forum: General Help
---

### Post by Suilenroc on 2008-11-17
Hey all, Suilenroc here. 

So I'm currently using this script to convert files from .m4a to .mp3:

```

sudo apt-get install id3v2 mplayer lame python-mutagen#!/usr/bin/python
#
#    Copyright (C) Brad Smith 2008
#
#    This file is ConvertToMP3
#
#    ConvertToMP3 is free software: you can redistribute it and/or modify
#    it under the terms of the GNU General Public License as published by
#    the Free Software Foundation, either version 3 of the License, or
#    (at your option) any later version.
#
#    ConvertToMP3 is distributed in the hope that it will be useful,
#    but WITHOUT ANY WARRANTY; without even the implied warranty of
#    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#    GNU General Public License for more details.
#
#    You should have received a copy of the GNU General Public License
#    along with Foobar.  If not, see <http://www.gnu.org/licenses/>.
#
#
# A script to convert non-DRM'd iTunes M4A files to MP3 so they will
# play with portable players that don't support M4A.
#
# Must install id3v2, mplayer, lame, python-mutagen

import commands, subprocess, os, sys, shutil
from mutagen.mp4 import MP4, MP4StreamInfoError
from mutagen.id3 import ID3, TIT2, TPE1, TALB, TRCK, TCON, TIT1, TYER, COMM

def getTag(tagInfo, primaryTag, secondaryTag = u""):
	tagData = u""
	if tagInfo.tags.has_key(primaryTag):
		tagData = tagInfo.tags[primaryTag]
	elif secondaryTag != u"" and tagInfo.tags.has_key(secondaryTag):
		tagData = tagInfo.tags[secondaryTag]

	while type(tagData) == list or type(tagData) == tuple:
		tagData = tagData[0]
	
	if type(tagData) != unicode:
		tagData = unicode(tagData)
	return tagData

def getFilesEnding(targetDir, endingIn):
	results = []
	for current, dirs, files in os.walk(targetDir, True):
		for f in files:
			if f.lower().endswith(endingIn):
				results.append(os.path.join(targetDir, current, f))
	return results

def main():
	errstrings = []
	
	if len(sys.argv) == 1:
		print "ERROR: This program must be run with the name of the directory containing the M4A files as the first argument.\n"
		print "Examples:"
		print "\t./ConvertToMP3.py /home/username/my_music"
		print "\t./ConvertToMP3.py /media/music /tmp/destination"
		sys.exit(1)
	
	copymp3s = False
	if "--copymp3s" in sys.argv:
		copymp3s = True
		sys.argv.remove("--copymp3s")
	
	convertdir = unicode(os.path.abspath(sys.argv[1]), 'UTF-8')
	print ("Attempting to convert M4A files in '" + convertdir + "'").encode('UTF-8')
	if not os.path.isdir(convertdir):
		print "ERROR: The argument '" + convertdir + "' is not a directory."
		sys.exit(2)
	
	destdir = os.path.normpath(convertdir) + u"_mp3"
	if len(sys.argv) == 3:
		destdir = unicode(os.path.abspath(sys.argv[2]), 'UTF-8')
	
	# If the directory doesn't exist, create it; otherwise, skip converting any files that already exist in the directory
	if os.path.isdir(destdir):
		print ("The destination directory '" + destdir + "' already exists. Conversion will be skipped for any MP3s that already exist.").encode('UTF-8')
	else:
		os.makedirs(destdir)
	
	copycount = 0
	if copymp3s == True:
		mp3s = getFilesEnding(convertdir, ".mp3")
		for mp3 in mp3s:
			sourcemp3 = os.path.normpath(os.path.join(convertdir, mp3))
			srcprefix = os.path.commonprefix([convertdir, sourcemp3])
			mp3postfix = mp3[len(srcprefix):]
			destmp3 = os.path.normpath(destdir + mp3postfix)
			destmp3dir = os.path.split(destmp3)[0]
			if not os.path.isdir(destmp3dir):
				os.makedirs(destmp3dir)
			if not os.path.isfile(destmp3):
				shutil.copy(sourcemp3, destmp3)
				copycount += 1
	
	m4as = getFilesEnding(convertdir, ".m4a")
	
	if len(m4as) == 0 or (len(m4as) == 1 and m4as[0] == u''):
		print "ERROR: No M4A files were found in the specified directory."
		sys.exit(3)
	
	print ("Converted MP3 files will be placed in '" + destdir + "'").encode('UTF-8')
	
	convertdict = {}
	for m4a in m4as:
		sourcem4a = os.path.normpath(os.path.join(convertdir, m4a))
		srcprefix = os.path.commonprefix([convertdir, sourcem4a])
		m4apostfix = m4a[len(srcprefix):]
		destm4a = os.path.normpath(destdir + m4apostfix)[:-4] + u'.mp3'
		convertdict[sourcem4a] = destm4a
	
	convertcount = 0
	skipcount = 0
	wav = u'/tmp/converttomp3_outfile.wav'
	for src in convertdict.keys():
		if not os.path.isfile(src):
			print ("ERROR: The file '" + src + "' does not exist. This should never happen; there must be an error in the program. Sorry :)").encode('UTF-8')
			sys.exit(5)
	
		dest = convertdict[src]
		if os.path.isfile(dest):
			print ("The file '" + dest + "' already exists. Conversion will be skipped.")
			skipcount += 1
			continue
		
		if not os.path.isdir(os.path.split(dest)[0]):
			os.makedirs(os.path.split(dest)[0])
	
		title = artist = album = track = genre = year = comment = group = u""
		try:
			tagInfo = MP4(src)
			title = getTag(tagInfo, '\xa9nam')
			artist = getTag(tagInfo, '\xa9ART', 'aART')
			album = getTag(tagInfo, '\xa9alb')
			track = getTag(tagInfo, 'trkn')
			genre = getTag(tagInfo, '\xa9gen')
			year = getTag(tagInfo, '\xa9day')
			comment = getTag(tagInfo, '\xa9cmt')
			group = getTag(tagInfo, '\xa9grp')
	
		except MP4StreamInfoError:
			errstrings.append("ERROR: The file '" + src + "' seems to have invalid song information tags. Unfortunately, this means that the resulting MP3 file will not have embedded tags.")
	
		try:
			subprocess.check_call([u'mplayer', u'-quiet', u'-ao', u'pcm', src, u'-ao', u'pcm:file=' + wav])
		except subprocess.CalledProcessError:
			errstrings.append("ERROR: The file '" + src + "' could not be converted to a WAV with mplayer. The file may be corrupt.")
			continue
		
		try:
			subprocess.check_call([u'lame', u'--quiet', u'-h', u'-b', u'192', wav, dest])
		except subprocess.CalledProcessError:
			errstrings.append("ERROR: The file '" + src + "' could not be converted to an MP3 with lame. An error has occurred.")
			continue

		destTagInfo = ID3()
		if title != u"":
			destTagInfo.add(TIT2(encoding=3, text=title))
		if artist != u"":
			destTagInfo.add(TPE1(encoding=3, text=artist))
		if album != u"":
			destTagInfo.add(TALB(encoding=3, text=album))
		if track != u"":
			destTagInfo.add(TRCK(encoding=3, text=track))
		if genre != u"":
			destTagInfo.add(TCON(encoding=3, text=genre))
		if year != u"":
			destTagInfo.add(TYER(encoding=3, text=year))
		if comment != u"":
			destTagInfo.add(COMM(encoding=3, text=comment))
		if group != u"":
			destTagInfo.add(TIT1(encoding=3, text=group))
		destTagInfo.save(dest)

		convertcount += 1
	
	
	if os.path.isfile(wav):
		os.remove(wav)
	
	print "\n\n**************************************************************************\n\n"
	if len(errstrings) == 0:
		print "Conversion succeeded! No errors occurred."
	else:
		print "The following errors took place during conversion:"
		for err in errstrings:
			print err.encode('UTF-8')
	if copycount > 0:
		print (str(copycount) + " MP3 files were copied from the source directory.").encode('UTF-8')
	if skipcount > 0:
		print (str(skipcount) + " MP3 files were not converted because they already existed in the destination directory.").encode('UTF-8')
	print (str(convertcount) + " MP3 files were created in the '" + destdir + "' directory.").encode('UTF-8')

if __name__ == '__main__':
	main()


```

It's not my script, it's from [http://pragmattica.wordpress.com/2008/01/17/convert-itunes-m4a-files-to-mp3-on-linux/](http://pragmattica.wordpress.com/2008/01/17/convert-itunes-m4a-files-to-mp3-on-linux/)


I have a Music folder, in which there are about 70 different artist folders. I want to know how to take all of those files out of folders into the above folder in one script.

Does anyone know how?

---

### Post by Suilenroc on 2008-11-17
Never mind all, figured it out. Used a simple find script that was then piped into an xargs.

---

