---
title: "Help with PS3 and fuppes"
date: 2008-07-22
forum: General Help
---

### Post by dannym978 on 2008-07-22
Hi, I am having trouble getting my PS3 to be able to see the available files on my laptop. The PS3 sees the fuppes server with no issues but when i try and view the available files i get the message 'no tracks available' on my PS3. I have included my fuppes.cfg file below in the hope someone may be able to identify the problem and help me get this working?


[PHP]

<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
<shared_objects>
<dir>/home/dan/Music</dir>
</shared_objects>
<network>
<!--empty = automatic detection-->
<interface>wlan0</interface>
<!--empty or 0 = random port-->
<http_port>0</http_port>
<!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
<allowed_ips>
<!--<ip>192.168.0.1</ip>-->
<ip>192.168.0.10</ip>
</allowed_ips>
</network>
<content_directory>
<!--a list of possible charsets can be found under:
http://www.gnu.org/software/libiconv/-->
<local_charset>UTF-8</local_charset>
<!--libs used for metadata extraction when building the database. [true|false]-->
<use_imagemagick>true</use_imagemagick>
<use_taglib>true</use_taglib>
<use_libavformat>true</use_libavformat>
</content_directory>
<transcoding>
<!--[lame|twolame]-->
<audio_encoder>lame</audio_encoder>
<!--[true|false]-->
<transcode_vorbis>true</transcode_vorbis>
<transcode_musepack>true</transcode_musepack>
<transcode_flac>true</transcode_flac>
</transcoding>
<device_settings>
<!--"default" settings are inhertied by specific devices and can be overwritten-->
<!--do NOT remove the "default" device settings-->
<device name="default">
<!--specify the maximum length for file names (0 or empty = unlimited)-->
<max_file_name_length>0</max_file_name_length>
<!--[file|container]-->
<playlist_style>file</playlist_style>
<show_childcount_in_title>false</show_childcount_in_title>
<enable_dlna>false</enable_dlna>
<transcoding_release_delay>4</transcoding_release_delay>
<file_settings>
<!--audio files-->
<file ext="mp3">
<type>AUDIO_ITEM</type>
<mime_type>audio/mpeg</mime_type>
<dlna>MP3</dlna>
</file>
<file ext="ogg">
<type>AUDIO_ITEM</type>
<mime_type>application/octet-stream</mime_type>
<transcode enabled="true">
<ext>mp3</ext>
<mime_type>audio/mpeg</mime_type>
<dlna>MP3</dlna>
<http_encoding>chunked</http_encoding>
<decoder>vorbis</decoder>
<encoder>lame</encoder>
<bitrate>192</bitrate>
<samplerate>44100</samplerate>
</transcode>
</file>
<file ext="mpc">
<type>AUDIO_ITEM</type>
<mime_type>application/octet-stream</mime_type>
<transcode enabled="true">
<ext>mp3</ext>
<mime_type>audio/mpeg</mime_type>
<dlna>MP3</dlna>
<http_encoding>chunked</http_encoding>
<decoder>musepack</decoder>
<encoder>lame</encoder>
<bitrate>192</bitrate>
<samplerate>44100</samplerate>
</transcode>
</file>
<file ext="wav">
<type>AUDIO_ITEM</type>
<mime_type>audio/x-wav</mime_type>
</file>
<file ext="flac">
<type>AUDIO_ITEM</type>
<mime_type>audio/x-flac</mime_type>
<transcode enabled="true">
<ext>mp3</ext>
<mime_type>audio/mpeg</mime_type>
<dlna>MP3</dlna>
<http_encoding>chunked</http_encoding>
<decoder>flac</decoder>
<encoder>lame</encoder>
<bitrate>192</bitrate>
<samplerate>44100</samplerate>
</transcode>
</file>
<file ext="wma">
<type>AUDIO_ITEM</type>
<mime_type>audio/x-ms-wma</mime_type>
<dlna>WMAFULL</dlna>
</file>
<!--image files-->
<file ext="jpg">
<ext>jpeg</ext>
<type>IMAGE_ITEM</type>
<mime_type>image/jpeg</mime_type>
<convert enabled="false">
<!--<dcraw enabled="true">-q 0</dcraw>-->
<ext>png</ext>
<mime_type>image/png</mime_type>
<height>0</height>
<width>0</width>
<!--set "greater" to "true" if you only want to resize images greater than "height" or "width"-->
<greater>false</greater>
<!--set "less" to "true" if you only want to resize images less than "height" or "width"-->
<less>false</less>
<!--set "less" and "greater" to "false" if you always want to resize-->
</convert>
</file>
<file ext="bmp">
<type>IMAGE_ITEM</type>
<mime_type>image/bmp</mime_type>
</file>
<file ext="png">
<type>IMAGE_ITEM</type>
<mime_type>image/png</mime_type>
</file>
<file ext="gif">
<type>IMAGE_ITEM</type>
<mime_type>image/gif</mime_type>
</file>

<!--video files-->
<file ext="mpg">
<ext>mpeg</ext>
<type>VIDEO_ITEM</type>
<mime_type>video/mpeg</mime_type>
</file>
<file ext="mp4">
<type>VIDEO_ITEM</type>
<mime_type>video/mp4</mime_type>
</file>
<file ext="avi">
<type>VIDEO_ITEM</type>
<mime_type>video/x-msvideo</mime_type>
</file>
<file ext="wmv">
<type>VIDEO_ITEM</type>
<mime_type>video/x-ms-wmv</mime_type>
</file>
<file ext="vob">
<type>VIDEO_ITEM</type>
<mime_type>video/x-ms-vob</mime_type>
</file>
<file ext="vdr">
<type>VIDEO_ITEM</type>
<mime_type>video/x-extension-vdr</mime_type>
<transcode enabled="true">
<ext>vob</ext>
<mime_type>video/x-ms-vob</mime_type>
</transcode>
</file>
<file ext="flv">
<type>VIDEO_ITEM</type>
<mime_type>application/x-flash-video</mime_type>
</file>
<file ext="asf">
<type>VIDEO_ITEM</type>
<mime_type>video/x-ms-asf</mime_type>
</file>
<!--playlists-->
<file ext="pls">
<type>PLAYLIST</type>
<mime_type>audio/x-scpls</mime_type>
</file>
<file ext="m3u">
<type>PLAYLIST</type>
<mime_type>audio/x-mpegurl</mime_type>
</file>
</file_settings>
</device>
<!--If you have more than one device it is a good idea to set the ip address manually as some devices may have conflicting "user agents".-->
<!--It is safe to remove unneeded devices-->
<device name="PS3" enabled="true">
<user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
<user_agent>PLAYSTATION3</user_agent>
<!--<ip>192.168.0.10</ip>-->
<enable_dlna>true</enable_dlna>
<transcoding_release_delay>50</transcoding_release_delay>
<file_settings>
<file ext="ogg">
<type>item.audioItem.musicTrack</type>
<transcode enabled="true">
<http_encoding>stream</http_encoding>
</transcode>
</file>
<file ext="mpg">
<type>VIDEO_ITEM</type>
<transcode enabled="true">
<transcoder>ffmpeg</transcoder>
<mime_type>video/mpeg</mime_type>
<ext>mpg</ext>
<video_codec>copy</video_codec>
<audio_codec>mp2</audio_codec>
<audio_samplerate>44100</audio_samplerate>
<audio_bitrate>192000</audio_bitrate>
</transcode>
</file>
<file ext="avi">
<type>VIDEO_ITEM</type>
<mime_type>video/x-divx</mime_type>
<transcode enabled="true">
<transcoder>ffmpeg</transcoder>
<ext>mpg</ext>
<mime_type>video/mpeg</mime_type>
<video_codec vcodec="msmpeg4">mpeg1video</video_codec>
<video_bitrate>1800000</video_bitrate>
<audio_codec acodec="wmav2">mp2</audio_codec>
<audio_samplerate>44100</audio_samplerate>
<audio_bitrate>192000</audio_bitrate>
</transcode>
</file>
<file ext="mkv">
<type>VIDEO_ITEM</type>
<mime_type>video/x-matroska</mime_type>
<transcode enabled="true">
<transcoder>ffmpeg</transcoder>
<ext>mpg</ext>
<mime_type>video/mpeg</mime_type>
<video_codec>mpeg2video</video_codec>
<video_bitrate>1800000</video_bitrate>
<audio_codec>mp2</audio_codec>
<audio_samplerate>44100</audio_samplerate>
<audio_bitrate>192000</audio_bitrate>
</transcode>
</file>
<file ext="avi">
<type>VIDEO_ITEM</type>
<mime_type>video/x-msvideo</mime_type>
<transcode enabled="true">
<transcoder>ffmpeg</transcoder>
<ext>mpg</ext>
<mime_type>video/mpeg</mime_type>
<video_codec>mpeg2video</video_codec>
<video_bitrate>1800000</video_bitrate>
<audio_codec>mp2</audio_codec>
<audio_samplerate>44100</audio_samplerate>
<audio_bitrate>192000</audio_bitrate>
</transcode>
</file>
</file_settings>
</device>
<device name="Xbox 360" virtual="Xbox 360" enabled="false">
<user_agent>Xbox/2.0.\d+.\d+ UPnP/1.0 Xbox/2.0.\d+.\d+</user_agent>
<user_agent>Xenon</user_agent>
<xbox360>true</xbox360>
</device>
<device name="Noxon audio" virtual="default" enabled="false">
<!--Please enter the address of your Noxon. Automatic detection is impossible because the Noxon does not send a "user-agent" in it's requests-->
<!--<ip></ip>-->
<playlist_style>container</playlist_style>
<show_childcount_in_title>true</show_childcount_in_title>
</device>
<device name="Telegent TG 100" virtual="default" enabled="false">
<user_agent>dma/1.0 \(http://www.cybertan.com.tw/\)</user_agent>
<user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
<playlist_style>file</playlist_style>
<max_file_name_length>101</max_file_name_length>
</device>
</device_settings>
</fuppes_config>[/PHP]

---

### Post by cszikszoy on 2008-07-22
I was never able to get fuppes to work properly.

I've heard that ushare ([http://ushare.geexbox.org/](http://ushare.geexbox.org/)) works well for video and audio to both ps3 and xbox360.

For my 360 I just used another program called TVersity.  It's windows only so I have to run it inside of a VM.  It's not a very elegant solution, but it works, and I didn't really feel like messing with config files anymore.

Give ushare a try and let me know how it works for you.  I'm curious to see what your experience with it is.

---

### Post by dannym978 on 2008-07-22
No joy with ushare im afraid it says all my files are an unsupported format, even mp3s!

---

### Post by thomascrabs on 2008-07-22
Got fuppes working with PS3. Config attached. Hope it helps. Only thing I can suggest it trying to use your actual IP address rather than the name as I have had problems with using the name.

I couldn't get it to work at first but that was cos firestarter was blocking it! Took hours to realise that! doh!


[PHP]<?xml version="1.0" encoding="UTF-8"?>
<fuppes_config version="0.7.2.3">
  <shared_objects>
    <!--<dir>/mnt/music</dir>-->
    <!--<itunes>/Users/.../iTunes.xml</itunes>-->
    <dir>/media/hda5/Media/Music</dir>
    <dir>/media/hda5/Media/My Pictures</dir>
    <dir>/media/hda5/Media/Videos</dir>
  </shared_objects>
  <network>
    <!--empty = automatic detection-->
    <interface>192.168.1.3</interface>
    <!--empty or 0 = random port-->
    <http_port>5555</http_port>
    <!--list of ip addresses allowed to access fuppes. if empty all ips are allowed-->
    <allowed_ips>
      <!--<ip></ip>-->
    </allowed_ips>
  </network>
  <content_directory>
    <!--a list of possible charsets can be found under:
      http://www.gnu.org/software/libiconv/-->
    <local_charset>UTF-8</local_charset>
    <!--libs used for metadata extraction when building the database. [true|false]-->
    <use_imagemagick>true</use_imagemagick>
    <use_taglib>true</use_taglib>
    <use_libavformat>true</use_libavformat>
  </content_directory>
  <transcoding>
    <!--[lame|twolame]-->
    <audio_encoder>lame</audio_encoder>
    <!--[true|false]-->
    <transcode_vorbis>true</transcode_vorbis>
    <transcode_musepack>true</transcode_musepack>
    <transcode_flac>true</transcode_flac>
  </transcoding>
  <device_settings>
    <!--"default" settings are inhertied by specific devices and can be overwritten-->
    <!--do NOT remove the "default" device settings-->
    <device name="default">
      <!--specify the maximum length for file names (0 or empty = unlimited)-->
      <max_file_name_length>0</max_file_name_length>
      <!--[file|container]-->
      <playlist_style>file</playlist_style>
      <show_childcount_in_title>false</show_childcount_in_title>
      <enable_dlna>false</enable_dlna>
      <transcoding_release_delay>4</transcoding_release_delay>
      <file_settings>
        <!--audio files-->
        <file ext="mp3">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/mpeg</mime_type>
          <dlna>MP3</dlna>
        </file>
        <file ext="ogg">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>stream</http_encoding>
            <decoder>vorbis</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="mpc">
          <type>AUDIO_ITEM</type>
          <mime_type>application/octet-stream</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>stream</http_encoding>
            <decoder>musepack</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wav">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-wav</mime_type>
        </file>
        <file ext="flac">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-flac</mime_type>
          <transcode enabled="true">
            <ext>mp3</ext>
            <mime_type>audio/mpeg</mime_type>
            <dlna>MP3</dlna>
            <http_encoding>stream</http_encoding>
            <decoder>flac</decoder>
            <encoder>lame</encoder>
            <bitrate>192</bitrate>
            <samplerate>44100</samplerate>
          </transcode>
        </file>
        <file ext="wma">
          <type>AUDIO_ITEM</type>
          <mime_type>audio/x-ms-wma</mime_type>
          <dlna>WMAFULL</dlna>
        </file>
        <!--image files-->
        <file ext="jpg">
          <ext>jpeg</ext>
          <type>IMAGE_ITEM</type>
          <mime_type>image/jpeg</mime_type>
          <convert enabled="false">
            <!--<dcraw enabled="true">-q 0</dcraw>-->
            <ext>png</ext>
            <mime_type>image/png</mime_type>
            <height>0</height>
            <width>0</width>
            <!--set "greater" to "true" if you only want to resize images greater than "height" or "width"-->
            <greater>false</greater>
            <!--set "less" to "true" if you only want to resize images less than "height" or "width"-->
            <less>false</less>
            <!--set "less" and "greater" to "false" if you always want to resize-->
          </convert>
        </file>
        <file ext="bmp">
          <type>IMAGE_ITEM</type>
          <mime_type>image/bmp</mime_type>
        </file>
        <file ext="png">
          <type>IMAGE_ITEM</type>
          <mime_type>image/png</mime_type>
        </file>
        <file ext="gif">
          <type>IMAGE_ITEM</type>
          <mime_type>image/gif</mime_type>
        </file>
        <!--video files-->
        <file ext="mpg">
          <ext>mpeg</ext>
          <type>VIDEO_ITEM</type>
          <mime_type>video/mpeg</mime_type>
        </file>
        <file ext="mp4">
          <type>VIDEO_ITEM</type>
          <mime_type>video/mp4</mime_type>
        </file>
        <file ext="avi">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-msvideo</mime_type>
        </file>
        <file ext="wmv">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-wmv</mime_type>
        </file>
        <file ext="vob">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-vob</mime_type>
        </file>
        <file ext="vdr">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-extension-vdr</mime_type>
          <transcode enabled="true">
            <ext>vob</ext>
            <mime_type>video/x-ms-vob</mime_type>
          </transcode>
        </file>
        <file ext="flv">
          <type>VIDEO_ITEM</type>
          <mime_type>application/x-flash-video</mime_type>
        </file>
        <file ext="asf">
          <type>VIDEO_ITEM</type>
          <mime_type>video/x-ms-asf</mime_type>
        </file>
        <!--playlists-->
        <file ext="pls">
          <type>PLAYLIST</type>
          <mime_type>audio/x-scpls</mime_type>
        </file>
        <file ext="m3u">
          <type>PLAYLIST</type>
          <mime_type>audio/x-mpegurl</mime_type>
        </file>
      </file_settings>
    </device>
    <!--If you have more than one device it is a good idea to set the ip address manually as some devices may have conflicting "user agents".-->
    <!--It is safe to remove unneeded devices-->
    <device name="PS3" enabled="true">
      <user_agent>UPnP/1.0 DLNADOC/1.00</user_agent>
      <user_agent>PLAYSTATION3</user_agent>
      <!--<ip>192.168.1.8</ip>-->
      <enable_dlna>true</enable_dlna>
      <transcoding_release_delay>50</transcoding_release_delay>
      <file_settings>
        <file ext="ogg">
          <type>AUDIO_ITEM_MUSIC_TRACK</type>
          <transcode enabled="true">
            <http_encoding>stream</http_encoding>
          </transcode>
        </file>
      </file_settings>
    </device>
  </device_settings>
</fuppes_config>[/PHP]

---

### Post by thomascrabs on 2008-07-22
Also, are you getting DLNA errors and what format of file are you trying to find / play?

---

### Post by dannym978 on 2008-07-26
Thanks guys, in the end i ended up installing mediatomb, works great!

---

