---
title: "Mediatomb Ubuntu 9.04 - PS3 &quot;There are no tracks&quot;"
date: 2009-04-18
forum: Installation &amp; Upgrades
---

### Post by _francis on 2009-04-18
I had a working mediatomb installation until I decided to upgrade to 9.04beta today. (Never touch a running system - I know)

I used to start mediatomb as user, so my config.xml file is in the home folder.

Mediatomb was working sufficiently ( I could watch all my movies via mediatomb but never got it to show me thumbnails of my videos)

today I updated to 9.04 and now I get "There are no tracks" whenever I want to access my Video or Photo folder on the PS3.

I set up my mediatomb following more or less (took mediatomb from repositories instead of compiling it myself) the guide on [http://juliensimon.blogspot.com/search?q=mediatomb]("http://juliensimon.blogspot.com/search?q=mediatomb")

I checked filepermissions like suggested here[http://ubuntuforums.org/showthread.php?p=6841768]("http://ubuntuforums.org/showthread.php?p=6841768")

and, in a desperate attempt to get things working, I also tested ps3mediaserver - which i found here [http://ubuntuforums.org/showthread.php?t=995584]("http://ubuntuforums.org/showthread.php?t=995584") But the same results - MP3 works and for images and videos there is always the same message: There are no tracks

It looks like I didn't assign any files to the database - but I didn't change anything there and it looks good - I can see all the subfolders created from the database, but no vids or images.

My guess, but I m not very experienced with this stuff, is that there is something wrong with the transcode thing in 9.04. What I do not get is why images are affected too...
Now I m stuck and don't really know how to tackle this problem - Any suggestions!?

PLZ

EDIT: Reinstalled vlc, ffmpeg and mediatomb - slept over it - now it's working again

Here is my config.xml file - but I didn't change anything lately:

```
<?xml version="1.0" encoding="UTF-8"?>
<config version="1" xmlns="http://mediatomb.cc/config/1" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://mediatomb.cc/config/1 http://mediatomb.cc/config/1.xsd">
 <server>
  <ui enabled="yes" show-tooltips="yes">
     <accounts enabled="no" session-timeout="30">
       <account user="mediatomb" password="mediatomb"/>
     </accounts>
  </ui>

   <name>MediaTomb</name>
   <udn>uuid:b8b13d59-378e-4cb8-9a87-14f70c70f847</udn>
   <home>/home/media/.mediatomb</home>
   <webroot>/usr/share/mediatomb/web</webroot>
   
   <storage>
     <sqlite3 enabled="yes">
       <database-file>mediatomb.db</database-file>
     </sqlite3>
   </storage>
   
   <protocolInfo extend="yes"/><!-- For PS3 support change to "yes" -->
  
   <extended-runtime-options>
     <ffmpegthumbnailer enabled="yes">
       <thumbnail-size>128</thumbnail-size>
       <seek-percentage>5</seek-percentage>
       <filmstrip-overlay>yes</filmstrip-overlay>
       <workaround-bugs>no</workaround-bugs>
     </ffmpegthumbnailer>
     <mark-played-items enabled="no" suppress-cds-updates="yes">
       <string mode="prepend">*</string>
     </mark-played-items>
   </extended-runtime-options>

 </server>

 <import hidden-files="no">
   <scripting script-charset="UTF-8">
     <common-script>/usr/share/mediatomb/js/common.js</common-script>
     <playlist-script>/usr/share/mediatomb/js/playlists.js</playlist-script>
     <virtual-layout type="js">
       <import-script>/usr/share/mediatomb/js/import.js</import-script>
       <dvd-script>/usr/share/mediatomb/js/import-dvd.js</dvd-script>
     </virtual-layout>
   </scripting>
   <mappings>
     <extension-mimetype ignore-unknown="no">
       <map from="mp3" to="audio/mpeg"/>
       <map from="ogg" to="application/ogg"/>
       <map from="asf" to="video/x-ms-asf"/>
       <map from="asx" to="video/x-ms-asf"/>
       <map from="wma" to="audio/x-ms-wma"/>
       <map from="wax" to="audio/x-ms-wax"/>
       <map from="wmv" to="video/x-ms-wmv"/>
       <map from="wvx" to="video/x-ms-wvx"/>
       <map from="wm" to="video/x-ms-wm"/>
       <map from="wmx" to="video/x-ms-wmx"/>
       <map from="m3u" to="audio/x-mpegurl"/>
       <map from="pls" to="audio/x-scpls"/>
       <map from="flv" to="video/x-flv"/>
       <map from="avi" to="video/divx"/>
       <map from="mkv" to="video/x-matroska"/>
       <map from="mts" to="video/mpeg"/>
       <map from="ts" to="video/mpeg"/>
       <map from="m2ts" to="video/mpeg"/>
       <map from="flac" to="audio/x-flac"/>
       <map from="mov" to="video/x-quicktime"/>
       <map from="vob" to="video/mpeg"/>
       <map from="m4v" to="video/mp4"/>
       <map from="iso" to="application/x-iso9660-image"/>
       <map from="gif" to="image/gif"/>
       <map from="jpg" to="image/jpeg"/>
       <map from="png" to="image/png"/>
       <map from="mp4" to="video/mp4"/>
       <map from="mp4a" to="video/mp4"/>
       <map from="3gp" to="video/3gpp"/>
     </extension-mimetype>
     
    <mimetype-upnpclass>
       <map from="audio/*" to="object.item.audioItem.musicTrack"/>
       <map from="video/*" to="object.item.videoItem"/>
       <map from="application/x-iso9660-image" to="object.item.videoItem"/>
       <map from="image/*" to="object.item.imageItem"/>
     </mimetype-upnpclass>
   
     <mimetype-contenttype>
       <treat mimetype="audio/mpeg" as="mp3"/>
       <treat mimetype="application/ogg" as="ogg"/>
       <treat mimetype="audio/x-flac" as="flac"/>
       <treat mimetype="image/jpeg" as="jpg"/>
       <treat mimetype="audio/x-mpegurl" as="playlist"/>
       <treat mimetype="audio/x-scpls" as="playlist"/>
       <treat mimetype="audio/x-wav" as="pcm"/>
       <treat mimetype="video/x-msvideo" as="avi"/>
       <treat mimetype="video/divx" as="avi"/>
       <treat mimetype="video/mp4" as="mp4"/>
       <treat mimetype="audio/mp4" as="mp4"/>
       <treat mimetype="video/quicktime" as="mov"/>
       <treat mimetype="video/x-quicktime" as="mov"/>
       <treat mimetype="application/x-iso9660-image" as="dvd"/>
     </mimetype-contenttype>
   
  </mappings>
  
   <online-content>
     <!-- Make sure to setup a transcoding profile for flv -->
     <YouTube enabled="yes" refresh="28800" update-at-start="yes" purge-after="604800" racy-content="exclude">
       <favorites user="XXXX"/>
       <playlists user="XXXX"/>
       <uploads user="XXXX">
       <standardfeed feed="most_viewed" time-range="today"/>
       <standardfeed feed="top_rated" time-range="this_week"/>
     </YouTube>
     <AppleTrailers enabled="yes" refresh="43200" update-at-start="yes" resolution="640"/>
   </online-content>
 </import>

 <transcoding enabled="yes">
   <mimetype-profile-mappings>
 <transcode mimetype="application/ogg"   using="audio-generic"/>
 <transcode mimetype="audio/x-flac"      using="audio-generic"/>
 <transcode mimetype="video/x-ms-asf"    using="video-generic"/>
 <transcode mimetype="video/x-flv"       using="video-generic"/>
 <transcode mimetype="video/x-matroska"  using="video-generic"/>
 <transcode mimetype="video/x-quicktime" using="video-generic"/>
 <transcode mimetype="video/quicktime"   using="video-generic"/>

 <transcode mimetype="video/x-ms-asf"    using="image-generic"/>
 <transcode mimetype="video/x-flv"       using="image-generic"/>
 <transcode mimetype="video/x-matroska"  using="image-generic"/>
 <transcode mimetype="video/x-quicktime" using="image-generic"/>
 <transcode mimetype="video/quicktime"   using="image-generic"/>
 <transcode mimetype="video/divx"	 using="image-generic"/>	


   </mimetype-profile-mappings>
   <profiles>

      <profile name="audio-generic" enabled="yes" type="external" >
       <mimetype>audio/L16</mimetype>
       <first-resource>yes</first-resource>
       <accept-url>yes</accept-url>
       <sample-frequency>44100</sample-frequency>
       <audio-channels>2</audio-channels>
       <accept-ogg-theora>no</accept-ogg-theora>
       <hide-original-resource>yes</hide-original-resource>
       <agent command="ffmpeg" arguments="-ac 2 -ar 44100 -y -i %in -f s16be %out"/>
       <buffer size="1048576" chunk-size="4096" fill-size="1024"/>
      </profile>

     <profile name="video-generic" enabled="yes" type="external">
       <avi-fourcc-list mode="ignore">
            <fourcc>DX50</fourcc>
            <fourcc>DM4V</fourcc>
            <fourcc>M4S2</fourcc>
       </avi-fourcc-list>
       <mimetype>video/mpeg</mimetype>
       <accept-url>yes</accept-url>
       <first-resource>yes</first-resource>
       <hide-original-resource>yes</hide-original-resource>
       <accept-ogg-theora>yes</accept-ogg-theora>
       <agent command="/usr/local/bin/mediatomb-video-generic.sh" arguments="%in %out"/>
       <buffer size="1048576" chunk-size="26214" fill-size="52428"/>

       <profile name="image-generic" enabled="yes" type="external">
        <mimetype>image/jpeg</mimetype>
        <accept-url>no</accept-url>
        <thumbnail>yes</thumbnail>
        <resolution>160x160</resolution>
        <agent command="ffmpegthumbnailer" arguments="-i %in -o %out -s 160"/>
        <buffer size="524288" chunk-size="512" fill-size="1024"/>
      </profile>


     </profile>

   </profiles>
 </transcoding>
 
 <lastfm enabled="yes"> 
 <username>XXXX</username> 
 <password>XXXX</password> 
 </lastfm> 

</config>
```

---

