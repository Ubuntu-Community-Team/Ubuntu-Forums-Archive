---
title: "Xmms fonts are too little"
date: 2004-10-18
forum: Installation &amp; Upgrades
---

### Post by szerencsefia on 2004-10-18
I have install by apt-get the xmms and my fonts are too little to read. This is my xmms config file:
```

[xmms]
allow_multiple_instances=FALSE
use_realtime=FALSE
always_show_cb=TRUE
convert_underscore=TRUE
convert_%20=TRUE
show_numbers_in_pl=TRUE
snap_windows=TRUE
save_window_positions=TRUE
dim_titlebar=TRUE
use_pl_metadata=TRUE
get_info_on_load=FALSE
get_info_on_demand=TRUE
eq_doublesize_linked=TRUE
no_playlist_advance=FALSE
sort_jump_to_file=FALSE
smooth_title_scroll=TRUE
use_backslash_as_dir_delimiter=FALSE
player_x=877
player_y=27
player_shaded=TRUE
player_visible=TRUE
shuffle=FALSE
repeat=FALSE
doublesize=FALSE
autoscroll_songname=TRUE
timer_mode=0
vis_type=1
analyzer_mode=0
analyzer_type=1
analyzer_peaks=TRUE
scope_mode=0
vu_mode=1
vis_refresh_rate=0
analyzer_falloff=3
peaks_falloff=1
playlist_x=877
playlist_y=55
playlist_width=275
playlist_height=203
playlist_shaded=TRUE
playlist_visible=TRUE
playlist_transparent=FALSE
playlist_font=-adobe-helvetica-bold-r-*-*-10-*
use_fontsets=FALSE
mainwin_use_xfont=FALSE
mainwin_font=-adobe-helvetica-medium-r-*-*-8-*
playlist_position=0
equalizer_x=877
equalizer_y=41
snap_distance=10
equalizer_visible=TRUE
equalizer_shaded=TRUE
equalizer_active=TRUE
equalizer_autoload=FALSE
easy_move=FALSE
use_eplugins=FALSE
always_on_top=FALSE
sticky=FALSE
equalizer_preamp=-1.11022e-15
random_skin_on_play=FALSE
pause_between_songs=FALSE
pause_between_songs_time=2
mouse_wheel_change=8
show_wm_decorations=FALSE
eqpreset_default_file=dir_default.preset
eqpreset_extension=preset
equalizer_band0=5.6
equalizer_band1=5.6
equalizer_band2=4
equalizer_band3=-1.11022e-15
equalizer_band4=-1.11022e-15
equalizer_band5=-1.11022e-15
equalizer_band6=-1.11022e-15
equalizer_band7=4.8
equalizer_band8=6.4
equalizer_band9=6.4
output_plugin=/usr/lib/xmms/Output/libOSS.so
disabled_iplugins=
url_history_length=0
generic_title_format=%p - %t
skin=/usr/share/xmms/Skins/Titanium

[Crossfade]
output_method=0
audio_device=0
use_alt_audio_device=FALSE
alt_audio_device=/dev/dsp
mixer_device=0
output_plugin=libOSS.so
op_config_string=libOSS.so=0,1,2304,0; libdisk_writer.so=1,0,2304,1
buffer_size=10000
sync_size=250
preload_size=0
songchange_timeout=500
enable_mixer=TRUE
mixer_reverse=FALSE
enable_debug=FALSE
enable_monitor=FALSE
oss_buffer_size=0
oss_preload_size=250
oss_mixer_use_master=FALSE
gap_lead_enable=TRUE
gap_lead_len_ms=500
gap_lead_level=512
gap_trail_enable=TRUE
gap_trail_len_ms=500
gap_trail_level=512
gap_trail_locked=1
buffer_size_auto=TRUE
album_detection=TRUE
http_workaround=FALSE
enable_op_max_used=FALSE
op_max_used_ms=250
effect_plugin=libnormvol.so
effect_enable=FALSE
output_rate=44100
oss_maxbuf_enable=FALSE
use_alt_mixer_device=FALSE
oss_fragments=22
oss_fragment_size=12
output_keep_opened=FALSE
mixer_software=FALSE
mixer_vol_left=75
mixer_vol_right=75
no_xfade_if_same_file=FALSE
alt_mixer_device=/dev/mixer
gap_crossing=TRUE
fc_xfade=5,2000,6000,1,4000,0,3,3,-6000,1,0,4000,33,0,0,0,0,0
fc_manual=4,2000,1000,1,500,0,3,3,-500,1,0,500,50,0,500,0,500,0
fc_album=2,0,0,0,0,0,0,0,0,0,0,1000,0,0,0,0,0,0
fc_start=6,0,0,0,0,0,0,0,0,0,0,100,0,0,0,0,0,0
fc_stop=7,0,0,0,100,0,0,0,500,0,0,0,0,0,0,0,0,0
fc_eop=7,0,0,0,100,0,0,0,500,0,0,0,0,0,0,0,0,0
fc_seek=4,0,50,0,0,0,0,0,0,0,0,1000,0,0,0,0,0,0
fc_pause=9,0,0,1,100,0,0,0,100,0,1,100,0,0,0,0,0,0

```
What shall I change to make normal font in the xmms?

---

### Post by FLeiXiuS on 2004-10-18
Right click on the player and select preferences.  Then go to fonts and select a font size that is larger.  This should do it for you.  If not try a different font.

---

### Post by szerencsefia on 2004-10-18
[quote=FLeiXiuS]Right click on the player and select preferences.  Then go to fonts and select a font size that is larger.  This should do it for you.  If not try a different font.[/quote]
thanks, I have tried diffrent font setup but the problem is same. Actually I got the problem in the main menu. I mean the fonts are too small in the option menu and in other menus from that. Have you other idea?
The problem is being in Gnome either in Xfce4.

---

### Post by BIN.anomaly on 2004-10-18
Try to run GConf (Applications &gt; Run Application... - &gt; gconf-editor ),  then choose: desktop -&gt; gnome -&gt; fotnt_rendering   and change dpi  value to 100.

---

### Post by szerencsefia on 2004-10-18
[quote=BIN.anomaly]Try to run GConf (Applications &gt; Run Application... - &gt; gconf-editor ),  then choose: desktop -&gt; gnome -&gt; fotnt_rendering   and change dpi  value to 100.[/quote]
Thanks,
It is done in Xfce did not help. I will try in GNOME now.

---

### Post by Pawel on 2004-11-01
Hi,

Try to install Beep-Media-Player ("BMP is a multimedia player that currently uses a skinned user interface based on Winamp 2.x skins. It is based on ("forked from") XMMS.")

More info you can see at:
=> [http://www.sosdg.org/~larne/w/BMP_Homepage](http://www.sosdg.org/~larne/w/BMP_Homepage)

---

