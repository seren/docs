---
title: Device Keys
template: support.hbs
columns: two
devices: [ photon, core ]
order: 7
---

Device Key Management
===

An easy step-by-step walkthrough of Particle CLI commands to BACKUP, RESTORE and CHANGE Keys.

https://github.com/spark/particle-cli#particle-keys-doctor

{{#if core}}
You may need to use this guide if you suffer from: "My Core is flashing yellow/red (orange) lights after it connects to Wi-Fi (Decryption Error)"

More detailed info:
https://community.particle.io/t/troubleshooting-my-core-is-flashing-yellow-red-lights-after-it-connects-to-wifi/627
{{/if}}

### How to Backup/Save your Key:

1. Place your {{#if photon}}Photon{{/if}}{{#if core}}Core{{/if}} into DFU mode by holding Mode and tapping Reset, then continue holding Mode for about 3 seconds until the LED starts flashing Yellow.

2.Run the ``particle keys save mykey.der`` command. This will backup the key on your {{#if photon}}Photon{{/if}}{{#if core}}Core{{/if}} to the Home folder on your computer.  You can substitute your own naming convention for the *.der file if you wish.

### How to Restore/Load your Key:

1. Place your {{#if photon}}Photon{{/if}}{{#if core}}Core{{/if}} into DFU mode by holding Mode and tapping Reset, then continue holding Mode for about 3 seconds until the LED starts flashing Yellow.

2. Run the ``particle keys load mykey.der`` command. This will restore the key you saved previously to your Home directory to your {{#if photon}}Photon{{/if}}{{#if core}}Core{{/if}}.  The file may not necessarily be named mykey.der, substitute whatever you backed it up as previously with the ``particle keys save`` command.

### How to Change your Key:

If you have physical access to the {{#if photon}}Photon{{/if}}{{#if core}}Core{{/if}} in question, here's how to change the Key on it. Once you do that you can share the Public key with us and we'll get you up and running again on that {{#if photon}}Photon{{/if}}{{#if core}}Core{{/if}}.  You may not even need to share the key with us if it your {{#if photon}}Photon{{/if}}{{#if core}}Core{{/if}} connects to the Cloud after following this procedure.

Bare with me for these next steps! This is slightly complicated because of the great security implemented on the {{#if photon}}Photon{{/if}}{{#if core}}Core{{/if}}.

1. Before we can start, you're going to want to install the Particle CLI tool to make life easier! Please see the readme here: [Particle CLI](https://github.com/spark/particle-cli)

2. Once the CLI tool is installed the first thing you should do is login to your Particle account.  If you do not have an account yet, please set one up at https://build.particle.io/build .

3. To login on the Particle CLI, run the command `particle login` and follow the prompts for email and password.

4. Next we need to get the Device ID of your {{#if photon}}Photon{{/if}}{{#if core}}Core{{/if}}. Start by putting the {{#if photon}}Photon{{/if}}{{#if core}}Core{{/if}} into Listening Mode by resetting it, and then holding the Mode button for about 3 seconds until it starts blinking BLUE.

5. Next run the following command to get the ID of your {{#if photon}}Photon{{/if}}{{#if core}}Core{{/if}}: ``particle serial identify``. It should reply "Your {{#if photon}}photon{{/if}}{{#if core}}core{{/if}} id is: xxxxxxxxxxxxxxxxxx". Copy the number down or to your clipboard for later.

6. View the key commands and example output here for the next steps: https://github.com/spark/particle-cli#particle-keys-doctor

7. Place your {{#if photon}}Photon{{/if}}{{#if core}}Core{{/if}} into DFU mode by holding Mode and tapping Reset, then continue holding Mode for about 3 seconds until the LED starts flashing Yellow.

8. Run the ``particle keys doctor xxxxx`` command, where xxxxx is the device ID you copied just earlier. This will generate a new public/private key pair and automatically download it to your device, and also send the public key up to the Cloud.

9. For good measure, run this command to make sure the key has been sent to the Cloud ``particle keys send yyyyy xxxxx_new.pub.pem``, where yyyyy is your device ID and xxxxx is also the same device ID. Written this way to show you the first part is your device ID, and the second part is the ID in part of a filename of your public key that was auto generated by the `doctor` command.

10. Please email us a copy of your new Public key file (skip this if it connects to the Cloud already). It should be called xxxxx_new.pub.pem, where you guessed it...xxxxx is the device ID from before ;) You should be able to search your system hard drive for it pretty easily but it is typically found in your Home directory.

Congrats, you made it to the end! now your {{#if photon}}Photon{{/if}}{{#if core}}Core{{/if}} should be connected to the Cloud... or will be just as soon as we add your Key to the server.