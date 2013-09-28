
audio_ALC1150
============
OS X Realtek ALC1150 Onboard Audio

This guide enables OS X Realtek ALC1150 onboard audio on Intel based motherboards with a bootable clean install of OS X. The Realtek AppleHDA.kext only works with the codec the kext was edited for and patches the native AppleHDA.kext.
____________________________________________________________Download ZIP >  > 

Requirements
1. Native S/L/E/AppleHDA.kext (restore native AppleHDA.kext with Combo Update)
2. alc1150-85 - Mountain Lion 10.8.5/AppleHDA.kext_v2.4.7

Realtek ALC AppleHDA Guides https://github.com/toleda/audio_ALCInjection
ML-Realtek ALC AppleHDA Capabilities.pdf
ML-Realtek ALC AppleHDA Screenshots.pdf
ML-Customizing the Realtek AppleHDA.pdf

Two Realtek ALC1150 AppleHDA.kext Audio_IDs, select one
Audio_ID: 1 supports HD4600/AMD/Nvidia HDMI and 3, 5 and 6 port Realtek ALC onboard audio  
Audio_ID: 2 supports HD4600/AMD/Nvidia HDMI and 3 port Realtek ALC onboard audio
Audio_IDs: 1 and 2 support analog 5.1 surround sound, 3 does not
Audio_IDs: 1 and 2 require HDMI audio dsdt edits for HDMI audio 

Four techniques enable the Realtek ALC AppleHDA.kext, select one
http://www.insanelymac.com/forum/topic/290796-realtek-alc-applehda-audio-injection/
1. No dsdt/audio enabler = Audio_ID, install either kext (use 1a or 1b, not both)
1a. Audio_ID = 1/HDAEnabler1.kext https://github.com/toleda/audio_HDAEnabler1
1b. Audio_ID = 2/HDAEnabler2.kext https://github.com/toleda/audio_HDAEnabler2
2. dsdt/HDEF/layout-id = Audio_ID, see {Guide} Add or Edit dsdt/HDEF.pdf
2a. Audio_ID = 1/layout-id: 0x01, 0x00, 0x00, 0x00, 0x00
2b. Audio_ID = 2/layout-id: 0x02, 0x00, 0x00, 0x00, 0x00
2c. Audio_ID = 3, see dsdt/HD3K/HD4K HDMI audio
3. ssdt/HDEF/layout-id = Audio_ID, see {Guide} Add ssdt/HDEF.pdf
3a. Audio_ID = 1/layout-id: 0x01, 0x00, 0x00, 0x00, 0x00
3b. Audio_ID = 2/layout-id: 0x02, 0x00, 0x00, 0x00, 0x00
3c. Audio_ID = 3, see ssdt/HD3K/HD4K HDMI audio
4. Clover/Config.plist/PCI/HDAInjection, see ML-Clover Realtek ALC AppleHDA Injection.pdf
4a. Audio_ID = 1/HDAInjection=1
4b. Audio_ID = 2/HDAInjection=2
4c. Audio_ID = 3/HDAInjection=3 

Download
1. https://github.com/toleda/audio_ALC1150
2. Select: Download ZIP (above and right)

Installation/Shell Script
1. Downloads/audio_ALC1150-master/
1a. for 10.8.5/audio_alc1150-85_patch.command
2. Launch (double click: audio_alc1150-ver_patch.command)
3. Enter password at prompt
4. Save Log: Terminal/Shell/Export Text As../Terminal Saved Output/Desktop/audio_ALC1150
5. Restart

Troubleshooting
1. ML-Realtek ALC AppleHDA Capabilities.pdf
2. Post to http://www.insanelymac.com/forum/topic/290797-mountain-lion-realtek-alc-applehda-audio/
3. Post to http://www.tonymacx86.com/audio/76309-mountain-lion-multibeast-no-audio-solutions-problem-reporting.html

Credit
THe KiNG 
RevoGirl

toleda
https://github.com/toleda/audio_ALC1150
audio_alc1150-85_patch.command
README.txt
Files:
1150.zip

Details - audio_ALC1150-ver_patch script  (see Requirements)

1. Verify: 
1a. native S/L/E/AppleHDA.kext
1b. Downloads/audio_ALC1150-master

2. Rename or Delete (if present)
2a. Desktop/audio-ALC1150 to Desktop/audio-ALC1150-archive

3. Run script
3a. Downloads/audio_ALC1150-master/audio_alc1150-ver_patch
3b. Lunch (double click)
3c. Enter Password when requested

4. Example: Terminal/audio_alc1150-85_patch window
_____________________________

Last login: Sat Sep 14 15:54:19 on console
$ .../Downloads/audio_ALC1150-master/audio_alc1150-85_patch.command ; exit;
Prepare Desktop/audio_ALC1150 ...
Archive:  1150.zip
   creating: 1150/
  inflating: 1150/Info-85.plist      
 extracting: 1150/layout1.xml.zlib   
 extracting: 1150/layout2.xml.zlib    
  inflating: 1150/Platforms.xml.zlib  
Install files ...
Password:
Patch binary ...
Fix permissions ...
Kernel cache...
Finished, restart required.
logout

[Process completed]
___________________________

5. If output is the same, success.  
5a. Terminal/Shell/Export Text As../Terminal Saved Output/Desktop/audio_ALC1150
5b. Restart

6. If errors or a different output;
6a. Install Desktop/audio_ALC1150/AppleHDA-orig.kext to S/L/E/AppleHDA.kext
6b. Go to Step 1.

7. If boot problem caused by AppleHDA, Boot/Single User Mode/Terminal
sudo rm -R /System/Library/Extensions/AppleHDA.kext
