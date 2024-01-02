name: "🍿️ DualSubs: 🎦 Universal"
desc: "流媒体平台字幕增强及双语模块，如需恢复TV完整支持，请配合“ iRingo: 📺 TV app”使用"
openUrl: "http://boxjs.com/#/app/DualSubs.Universal"
author: "VirgilClyne"
homepage: "https://github.com/DualSubs"
manual: "https://github.com/DualSubs/Universal/wiki/🍿-DualSubs:-🎦-Universal"
icon: "https://github.com/DualSubs/Universal/raw/main/database/icon_rounded.png"

http:
  force-http-engine:
    - "*.hls.pv-cdn.net"
    - "*.hls.row.aiv-cdn.net"
    - "*avodhlss3ww-a.akamaihd.net"
    - "s3.amazonaws.com"
    - "cf-timedtext.aux.pv-cdn.net"
    - "d1v5ir2lpwr8os.cloudfront.net"
    - "d22qjgkvxw22r6.cloudfront.net"
    - "d25xi40x97liuc.cloudfront.net"
    - "d27xxe7juh1us6.cloudfront.net"
    - "dmqdd6hw24ucf.cloudfront.net"
    - "assets.huluim.com"
    - "vod-*.live.cf.md.bbci.co.uk"
    - "vod-*-live.akamaized.net"
  mitm:
    - "play-edge.itunes.apple.com"
    - "hls.itunes.apple.com"
    - "hls-svod.itunes.apple.com"
    - "play.itunes.apple.com"
    - "vod-*.tv.apple.com"
    - "*.media.dssott.com"
    - "*.media.starott.com"
    - "atv-ps.amazon.com"
    - "atv-ps-fe.primevideo.com"
    - "*.hls.pv-cdn.net"
    - "*.hls.row.aiv-cdn.net"
    - "*avodhlss3ww-a.akamaihd.net"
    - "s3.amazonaws.com"
    - "cf-timedtext.aux.pv-cdn.net"
    - "d1v5ir2lpwr8os.cloudfront.net"
    - "d22qjgkvxw22r6.cloudfront.net"
    - "d25xi40x97liuc.cloudfront.net"
    - "d27xxe7juh1us6.cloudfront.net"
    - "dmqdd6hw24ucf.cloudfront.net"
    - "*.prd.media.h264.io"
    - "manifests.api.hbo.com"
    - "manifests.v2.api.hbo.com"
    - "*.hbomaxcdn.com"
    - "vodmanifest.hulustream.com"
    - "manifest-dp.hulustream.com"
    - "livemanifest-f.hulustream.com"
    - "live-sc.hulustream.com"
    - "assets.huluim.com"
    - "assetshuluimcom-a.akamaihd.net"
    - "*-pplus.cbs.com"
    - "vod-*.cbsaavideo.com"
    - "vod-*.cbsivideo.com"
    - "*.airspace-*.cbsivideo.com"
    - "content-discovery.uplynk.com"
    - "x-default-stgec.uplynk.com"
    - "*-discovery1.uplynk.com"
    - "dplus-ph-prod-vod.akamaized.net"
    - "dplus-ph-google-v2.prod-vod.h264.io"
    - "*.stream.peacocktv.com"
    - "*.cdn.peacocktv.com"
    - "*-vod.fubo.tv"
    - "hls.ted.com"
    - "pubads.g.doubleclick.net"
    - "vod-*.live.cf.md.bbci.co.uk"
    - "vod-*-live.akamaized.net"
    - "api.britbox.com"
    - "*.content.britbox.co.uk"
    - "mecdn?.starz.com"
    - "manifest.prod.boltdns.net"
    - "ssaimanifest.prod.boltdns.net"
    - "amcplus-?.akamaized.net"
    - "redirector.playback.*.prod.deploys.brightcove.com"
    - "ap-hls-vod.dynamic.showtime.com"
    - "ap-hls-live.cdn?.showtime.com"
    - "*.cssott.com"
    - "manifest-viki.viki.io"
    - "api.viki.io"
    - "epixhls.akamaized.net"
    - "*.live.epix.services"
    - "media-production.nebula.app"
    - "*.prd.pluto.tv"
    - "*.plutotv.net"
  script:
    - match: ^https?:\/\/(play|play-edge|hls)\.itunes\.apple\.com\/WebObjects\/(MZPlay|MZPlayLocal)\.woa\/hls\/playlist\.m3u8
      name: DualSubs.Master.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/vod-(.+)-amt\.tv\.apple\.com\/itunes-assets\/(.+)\/([0-9a-f]{8}(-[0-9a-f]{4}){3}-[0-9a-f]{12})\/(.+)_subtitles\.m3u8\?(.*)subtype=
      name: DualSubs.Subtitles.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/vod-(.+)-amt\.tv\.apple\.com\/itunes-assets\/(.+)\/([0-9a-f]{8}(-[0-9a-f]{4}){3}-[0-9a-f]{12})\/(.+)\.webvtt\?(.*)subtype=(Official|External)
      name: DualSubs.Subtitles.Composite.response
      type: response
      require-body: true
    - match: ^https?:\/\/vod-(.+)-amt\.tv\.apple\.com\/itunes-assets\/(.+)\/([0-9a-f]{8}(-[0-9a-f]{4}){3}-[0-9a-f]{12})\/(.+)\.webvtt\?(.*)subtype=Translate
      name: DualSubs.Subtitles.Translate.response
      type: response
      require-body: true

    - match: ^https?:\/\/(play|play-edge|hls)\.itunes\.apple\.com\/WebObjects\/(MZPlay|MZPlayLocal)\.woa\/hls\/subscription\/playlist\.m3u8
      name: DualSubs.Master.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/(play|play-edge|hls)\.itunes\.apple\.com\/WebObjects\/(MZPlay|MZPlayLocal)\.woa\/hls\/subscription\/stream\/playlist\.m3u8\?(.*)subtype=
      name: DualSubs.Subtitles.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/vod-(.+)-svod\.tv\.apple\.com\/itunes-assets\/(.+)\/([0-9a-f]{8}(-[0-9a-f]{4}){3}-[0-9a-f]{12})\/(.+)_subtitles_V\d\.m3u8\?(.*)subtype=
      name: DualSubs.Subtitles.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/vod-(.+)-(aoc|svod)\.tv\.apple\.com\/itunes-assets\/(.+)\/([0-9a-f]{8}(-[0-9a-f]{4}){3}-[0-9a-f]{12})\/(.+)\.webvtt\?(.*)subtype=(Official|External)
      name: DualSubs.Subtitles.Composite.response
      type: response
      require-body: true
    - match: ^https?:\/\/vod-(.+)-(aoc|svod)\.tv\.apple\.com\/itunes-assets\/(.+)\/([0-9a-f]{8}(-[0-9a-f]{4}){3}-[0-9a-f]{12})\/(.+)\.webvtt\?(.*)subtype=Translate
      name: DualSubs.Subtitles.Translate.response
      type: response
      require-body: true

    - match: ^https?:\/\/(play|play-edge|hls)\.itunes\.apple\.com\/WebObjects\/(MZPlay|MZPlayLocal)\.woa\/hls\/workout\/playlist\.m3u8
      name: DualSubs.Master.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/(hls|hls-svod)\.itunes\.apple\.com\/itunes-assets\/(.+)\/([0-9a-f]{8}(-[0-9a-f]{4}){3}-[0-9a-f]{12})\/(.+)_subtitles_V\d\.m3u8
      name: DualSubs.Subtitles.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/(hls|hls-svod)\.itunes\.apple\.com\/itunes-assets\/(.+)\/([0-9a-f]{8}(-[0-9a-f]{4}){3}-[0-9a-f]{12})\/(.+)\.webvtt\?(.*)subtype=(Official|External)
      name: DualSubs.Subtitles.Composite.response
      type: response
      require-body: true
    - match: ^https?:\/\/(hls|hls-svod)\.itunes\.apple\.com\/itunes-assets\/(.+)\/([0-9a-f]{8}(-[0-9a-f]{4}){3}-[0-9a-f]{12})\/(.+)\.webvtt\?(.*)subtype=Translate
      name: DualSubs.Subtitles.Translate.response
      type: response
      require-body: true

    - match: ^https?:\/\/(.+)\.media\.(dssott|starott)\.com\/(.+\/)?ps01\/disney\/([0-9a-f]{8}(-[0-9a-f]{4}){3}-[0-9a-f]{12})\/(cbcs|ctr)-all-(.+)\.m3u8
      name: DualSubs.Master.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/(.+)\.media\.(dssott|starott)\.com\/(.+\/)?ps01\/disney\/([0-9a-f]{8}(-[0-9a-f]{4}){3}-[0-9a-f]{12})\/r\/(.*)(composite_(.+)|subtitles)\.m3u8\?(.*)subtype=
      name: DualSubs.Subtitles.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/(.+)\.media\.(dssott|starott)\.com\/(.+\/)?ps01\/disney\/([0-9a-f]{8}(-[0-9a-f]{4}){3}-[0-9a-f]{12})\/r\/(.+)\.vtt\?(.*)subtype=(Official|External)
      name: DualSubs.Subtitles.Composite.response
      type: response
      require-body: true
    - match: ^https?:\/\/(.+)\.media\.(dssott|starott)\.com\/(.+\/)?ps01\/disney\/([0-9a-f]{8}(-[0-9a-f]{4}){3}-[0-9a-f]{12})\/r\/(.+)\.vtt\?(.*)subtype=Translate
      name: DualSubs.Subtitles.Translate.response
      type: response
      require-body: true

    - match: ^https?:\/\/(.+)(\.(hls)\.(pv-cdn|row\.aiv-cdn)|avodhlss3ww-a\.akamaihd)\.net\/(.+)\/([0-9a-f]{8}(-[0-9a-f]{4}){3}-[0-9a-f]{12})\.m3u8
      name: DualSubs.Master.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/(.+)(\.(hls|dash)\.(pv-cdn|row\.aiv-cdn)|avodhlss3ww-a\.akamaihd)\.net\/(.+)\/([0-9a-f]{8}(-[0-9a-f]{4}){3}-[0-9a-f]{12})_subtitles\.m3u8\?(.*)subtype=
      name: DualSubs.Subtitles.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/(.+)(\.(hls|dash)\.(pv-cdn|row\.aiv-cdn)|avodhlss3ww-a\.akamaihd)\.net\/(.+)\/aiv-prod-timedtext\/(.+)\.m3u8\?(.*)subtype=
      name: DualSubs.Subtitles.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/s3\.amazonaws\.com\/aiv-prod-timedtext\/(.+)\/([0-9a-f]{8}(-[0-9a-f]{4}){3}-[0-9a-f]{12})\.m3u8\?(.*)subtype=
      name: DualSubs.Subtitles.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/(d1v5ir2lpwr8os|d22qjgkvxw22r6|d25xi40x97liuc|d27xxe7juh1us6|dmqdd6hw24ucf)\.cloudfront\.net\/(.+)\/([0-9a-f]{8}(-[0-9a-f]{4}){3}-[0-9a-f]{12})\.m3u8\?(.*)subtype=
      name: DualSubs.Subtitles.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/s3\.amazonaws\.com\/aiv-prod-timedtext\/(.+)\/([0-9a-f]{8}(-[0-9a-f]{4}){3}-[0-9a-f]{12})\.(vtt|ttml2)\?(.*)subtype=(Official|External)
      name: DualSubs.Subtitles.Composite.response
      type: response
      require-body: true
    - match: ^https?:\/\/(d1v5ir2lpwr8os|d22qjgkvxw22r6|d25xi40x97liuc|d27xxe7juh1us6|dmqdd6hw24ucf)\.cloudfront\.net\/(.+)\/([0-9a-f]{8}(-[0-9a-f]{4}){3}-[0-9a-f]{12})\.(vtt|ttml2)\?(.*)subtype=(Official|External)
      name: DualSubs.Subtitles.Composite.response
      type: response
      require-body: true
    - match: ^https?:\/\/s3\.amazonaws\.com\/aiv-prod-timedtext\/(.+)\/([0-9a-f]{8}(-[0-9a-f]{4}){3}-[0-9a-f]{12})\.(vtt|ttml2)\?(.*)subtype=Translate
      name: DualSubs.Subtitles.Translate.response
      type: response
      require-body: true
    - match: ^https?:\/\/(d1v5ir2lpwr8os|d22qjgkvxw22r6|d25xi40x97liuc|d27xxe7juh1us6|dmqdd6hw24ucf)\.cloudfront\.net\/(.+)\/([0-9a-f]{8}(-[0-9a-f]{4}){3}-[0-9a-f]{12})\.(vtt|ttml2)\?(.*)subtype=Translate
      name: DualSubs.Subtitles.Translate.response
      type: response
      require-body: true

    - match: ^https?:\/\/(cf|akm|gcp|fly|.+)\.pro?d\.media\.h264\.io\/r\/hls\.m3u8
      name: DualSubs.Master.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/(cf|akm|gcp|fly|.+)\.pro?d\.media\.h264\.io\/r\/hlsMedia\.m3u8\?(.*)subtype=
      name: DualSubs.Subtitles.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/(cf|akm|gcp|fly|.+)\.pro?d\.media\.h264\.io\/(.+)\.vtt\?(.*)subtype=(Official|External)
      name: DualSubs.Subtitles.Composite.response
      type: response
      require-body: true
    - match: ^https?:\/\/(cf|akm|gcp|fly|.+)\.pro?d\.media\.h264\.io\/(.+)\.vtt
      name: DualSubs.Subtitles.Translate.response
      type: response
      require-body: true

    - match: ^https?:\/\/manifests(\.v2)?\.api\.hbo\.com\/hls\.m3u8
      name: DualSubs.Master.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/manifests(\.v2)?\.api\.hbo\.com\/hlsMedia\.m3u8\?(.*)subtype=
      name: DualSubs.Subtitles.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/(.+)\.hbomaxcdn\.com\/videos\/(.+)\.vtt\?(.*)subtype=(Official|External)
      name: DualSubs.Subtitles.Composite.response
      type: response
      require-body: true
    - match: ^https?:\/\/(.+)\.hbomaxcdn\.com\/videos\/(.+)\.vtt\?(.*)subtype=Translate
      name: DualSubs.Subtitles.Translate.response
      type: response
      require-body: true

    - match: ^https?:\/\/vodmanifest\.hulustream\.com\/hulu\/v1\/hls\/multivariant\/(\d+)\/playlist\.m3u8
      name: DualSubs.Master.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/manifest-dp\.hulustream\.com\/hls\/(\d+)\.m3u8
      name: DualSubs.Master.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/vodmanifest\.hulustream\.com\/hulu\/v1\/hls\/vtt\/(\d+)\/playlist\.m3u8\?(.*)subtype=
      name: DualSubs.Subtitles.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/manifest-dp\.hulustream\.com\/webvtt\?(.*)subtype=
      name: DualSubs.Subtitles.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/(assets\.huluim\.com|assetshuluimcom-a\.akamaihd\.net)\/captions_webvtt\/(.+)\.vtt\?(.*)subtype=(Official|External)
      name: DualSubs.Subtitles.Composite.response
      type: response
      require-body: true
    - match: ^https?:\/\/(assets\.huluim\.com|assetshuluimcom-a\.akamaihd\.net)\/captions_webvtt\/(.+)\.vtt\?(.*)subtype=Translate
      name: DualSubs.Subtitles.Translate.response
      type: response
      require-body: true

    - match: ^https?:\/\/(vod-(.+)|(.+)\.airspace-(.+)|(.+)-pplus)\.(cbsaavideo|cbsivideo|cbs)\.com\/(.+)\/(master|manifest)\.m3u8
      name: DualSubs.Master.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/(vod-(.+)|(.+)\.airspace-(.+)|(.+)-pplus)\.(cbsaavideo|cbsivideo|cbs)\.com\/(.+)\/(stream_vtt|manifest_.*)\.m3u8\?(.*)subtype=
      name: DualSubs.Subtitles.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/(vod-(.+)|(.+)\.airspace-(.+)|(.+)-pplus)\.(cbsaavideo|cbsivideo|cbs)\.com\/(.+)\.vtt\?(.*)subtype=(Official|External)
      name: DualSubs.Subtitles.Composite.response
      type: response
      require-body: true
    - match: ^https?:\/\/cc\.cbs\.com\/closedcaption\/(.+)\.vtt\?(.*)subtype=(Official|External)
      name: DualSubs.Subtitles.Composite.response
      type: response
      require-body: true
    - match: ^https?:\/\/(vod-(.+)|(.+)\.airspace-(.+)|(.+)-pplus)\.(cbsaavideo|cbsivideo|cbs)\.com\/(.+)\.vtt\?(.*)subtype=Translate
      name: DualSubs.Subtitles.Translate.response
      type: response
      require-body: true
    - match: ^https?:\/\/cc\.cbs\.com\/closedcaption\/(.+)\.vtt\?(.*)subtype=Translate
      name: DualSubs.Subtitles.Translate.response
      type: response
      require-body: true

    - match: ^https?:\/\/content-discovery\.uplynk\.com\/(.+)\.m3u8
      name: DualSubs.Master.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/dplus-ph-(prod-vod\.akamaized\.net|google-v2\.prod-vod\.h264\.io)\/(.+)\/master\.m3u8
      name: DualSubs.Master.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/dplus-ph-(prod-vod\.akamaized\.net|google-v2\.prod-vod\.h264\.io)\/(.+)\/captions\.m3u8\?(.*)subtype=
      name: DualSubs.Subtitles.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/dplus-ph-(prod-vod\.akamaized\.net|google-v2\.prod-vod\.h264\.io)\/(.+)\.vtt\?(.*)subtype=(Official|External)
      name: DualSubs.Subtitles.Composite.response
      type: response
      require-body: true
    - match: ^https?:\/\/dplus-ph-(prod-vod\.akamaized\.net|google-v2\.prod-vod\.h264\.io)\/(.+)\.vtt\?(.*)subtype=Translate
      name: DualSubs.Subtitles.Translate.response
      type: response
      require-body: true

    - match: ^https?:\/\/(.+)\.cdn\.peacocktv\.com\/pub\/global\/(.+)\/cmaf\/(.+)\/master_cmaf\.m3u8
      name: DualSubs.Master.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/(.+)\.cdn\.peacocktv\.com\/pub\/global\/(.+)\/cmaf\/(.+)\/[^\/]*subtitles[^\/]*\.m3u8\?(.*)subtype=
      name: DualSubs.Subtitles.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/(.+)\.cdn\.peacocktv\.com\/pub\/global\/(.+)\/cmaf\/(.+)\/[^\/]*subtitles[^\/]*\.webvtt\?(.*)subtype=(Official|External)
      name: DualSubs.Subtitles.Composite.response
      type: response
      require-body: true
    - match: ^https?:\/\/(.+)\.cdn\.peacocktv\.com\/pub\/global\/(.+)\/cmaf\/(.+)\/[^\/]*subtitles[^\/]*\.webvtt
      name: DualSubs.Subtitles.Translate.response
      type: response
      require-body: true

    - match: ^https?:\/\/(.+)-vod\.fubo\.tv\/(.+)\/manifests\/master\.m3u8
      name: DualSubs.Master.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/(.+)-vod\.fubo\.tv\/(.+)\/manifests\/subtitles\/(.+)\/media\.m3u8\?(.*)subtype=
      name: DualSubs.Subtitles.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/(.+)-vod\.fubo\.tv\/(.+)\/manifests\/subtitles\/(.+)\.vtt\?(.*)subtype=(Official|External)
      name: DualSubs.Subtitles.Composite.response
      type: response
      require-body: true
    - match: ^https?:\/\/(.+)-vod\.fubo\.tv\/(.+)\/manifests\/subtitles\/(.+)\.vtt
      name: DualSubs.Subtitles.Translate.response
      type: response
      require-body: true

    - match: ^https?:\/\/hls\.ted\.com\/(.+)\/manifest\.m3u8
      name: DualSubs.Master.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/hls\.ted\.com\/(.+)\/subtitles\/(.+)\.m3u8\?(.*)subtype=
      name: DualSubs.Subtitles.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/hls\.ted\.com\/(.+)\/subtitles\/(.+)\.vtt\?(.*)subtype=(Official|External)
      name: DualSubs.Subtitles.Composite.response
      type: response
      require-body: true
    - match: ^https?:\/\/hls\.ted\.com\/(.+)\/subtitles\/(.+)\.vtt\?(.*)subtype=Translate
      name: DualSubs.Subtitles.Translate.response
      type: response
      require-body: true

    - match: ^https?:\/\/pubads\.g\.doubleclick\.net\/ondemand\/hls\/content\/(.+)\/master\.m3u8
      name: DualSubs.Master.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/pubads\.g\.doubleclick\.net\/ondemand\/hls\/content\/(.+)\/media\/tt-(.+)\.m3u8\?(.*)subtype=
      name: DualSubs.Subtitles.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/pubads\.g\.doubleclick\.net\/ondemand\/hls\/content\/(.+)\/(hls-webvtt|vtt)\/(.+)\.vtt\?(.*)subtype=(Official|External)
      name: DualSubs.Subtitles.Composite.response
      type: response
      require-body: true
    - match: ^https?:\/\/pubads\.g\.doubleclick\.net\/ondemand\/hls\/content\/(.+)\/(hls-webvtt|vtt)\/(.+)\.vtt
      name: DualSubs.Subtitles.Translate.response
      type: response
      require-body: true

    - match: ^https?:\/\/vod-hls-(.+)(\.live\.cf\.md\.bbci\.co\.uk|-live\.akamaized\.net)\/(.+)_hls_master\.m3u8
      name: DualSubs.Master.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/(.+)\.content\.britbox\.co\.uk\/(.+)\.ism\/\.m3u8
      name: DualSubs.Master.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/(.+)\.content\.britbox\.co\.uk\/(.+)\.ism\/(.+)-textstream(.+)\.m3u8\?(.*)subtype=
      name: DualSubs.Subtitles.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/(.+)\.content\.britbox\.co\.uk\/(.+)\.ism\/(.+)-textstream(.+)\.webvtt\?(.*)subtype=(Official|External)
      name: DualSubs.Subtitles.Composite.response
      type: response
      require-body: true
    - match: ^https?:\/\/(.+)\.content\.britbox\.co\.uk\/(.+)\/Subtitles\/(.+)\.vtt\?(.*)subtype=(Official|External)
      name: DualSubs.Subtitles.Composite.response
      type: response
      require-body: true
    - match: ^https?:\/\/(.+)\.content\.britbox\.co\.uk\/(.+)\.ism\/(.+)-textstream(.+)\.webvtt
      name: DualSubs.Subtitles.Translate.response
      type: response
      require-body: true
    - match: ^https?:\/\/(.+)\.content\.britbox\.co\.uk\/(.+)\/Subtitles\/(.+)\.vtt
      name: DualSubs.Subtitles.Translate.response
      type: response
      require-body: true

    - match: ^https?:\/\/api\.britbox\.com\/v1\/subtitles\?(.*)subtype=(Official|External)
      name: DualSubs.Subtitles.Composite.response
      type: response
      require-body: true
    - match: ^https?:\/\/api\.britbox\.com\/v1\/subtitles
      name: DualSubs.Subtitles.Translate.response
      type: response
      require-body: true

    - match: ^https?:\/\/(.+)\.starz\.com\/(.+)\/(.+)_HLS_(.+)\.m3u8
      name: DualSubs.Master.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/(.+)\.starz\.com\/(.+)\/captions\/(.+)\.m3u8\?(.*)subtype=
      name: DualSubs.Subtitles.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/(.+)\.starz\.com\/(.+)\/captions\/(.+)\.vtt\?(.*)subtype=(Official|External)
      name: DualSubs.Subtitles.Translate.response
      type: response
      require-body: true
    - match: ^https?:\/\/(.+)\.starz\.com\/(.+)\/captions\/(.+)\.vtt
      name: DualSubs.Subtitles.Translate.response
      type: response
      require-body: true

    - match: ^https?:\/\/ssaimanifest\.prod\.boltdns\.net\/(.+)\/playback\/once\/v1\/hls\/(.+)\/content\.m3u8
      name: DualSubs.Master.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/ssaimanifest\.prod\.boltdns\.net\/(.+)\/playback\/once\/v1\/hls\/(.+)\/subtitle_(.+)\/media\.m3u8\?(.*)subtype=
      name: DualSubs.Subtitles.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/amcplus-(.+)\.akamaized\.net\/composite-media\/v1\/hls\/(.+)\/segment(\d+)\.vtt\?(.*)subtype=(Official|External)
      name: DualSubs.Subtitles.Composite.response
      type: response
      require-body: true
    - match: ^https?:\/\/redirector\.playback\.(.+)\.prod\.deploys\.brightcove\.com\/v1\/(.+)\.vtt\?(.*)subtype=(Official|External)
      name: DualSubs.Subtitles.Composite.response
      type: response
      require-body: true
    - match: ^https?:\/\/amcplus-(.+)\.akamaized\.net\/composite-media\/v1\/hls\/(.+)\/segment(\d+)\.vtt\?(.*)subtype=Translate
      name: DualSubs.Subtitles.Translate.response
      type: response
      require-body: true
    - match: ^https?:\/\/redirector\.playback\.(.+)\.prod\.deploys\.brightcove\.com\/v1\/(.+)\.vtt
      name: DualSubs.Subtitles.Translate.response
      type: response
      require-body: true

    - match: ^https?:\/\/ap-hls-vod\.dynamic\.showtime\.com/(.+)\/(tv|mobile)_master\.m3u8
      name: DualSubs.Master.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/ap-hls-vod\.cdn\d\.showtime.com\/live\/sho(e|w)ast\/showtime.isml\.m3u8
      name: DualSubs.Master.m3u8.response
      type: response
      require-body: true

    - match: ^https?:\/\/(.+)\.cssott\.com\/(.+)\/mpeg_cbcs\/master_manifest_(.+)\.m3u8
      name: DualSubs.Master.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/(.+)\.cssott\.com\/(.+)\/mpeg_cbcs\/(.+)\/(.+)\.subtitles\.\d+\.m3u8
      name: DualSubs.Subtitles.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/(.+)\.cssott\.com\/(.+)\/mpeg_cbcs\/(.+)\/(.+)\.subtitles\.\d+\.split\.\d+\.webvtt\?(.*)subtype=(Official|External)
      name: DualSubs.Subtitles.Composite.response
      type: response
      require-body: true
    - match: ^https?:\/\/(.+)\.cssott\.com\/(.+)\/mpeg_cbcs\/(.+)\/(.+)\.subtitles\.\d+\.split\.\d+\.webvtt\?(.*)subtype=Translate
      name: DualSubs.Subtitles.Translate.response
      type: response
      require-body: true

    - match: ^https?:\/\/manifest-viki\.viki\.io\/(.+)\/manifest\.m3u8
      name: DualSubs.Master.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/manifest-viki\.viki\.io\/(.+)\/streams\/(.+)\/subtitles\.m3u8
      name: DualSubs.Subtitles.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/api\.viki\.io\/(.+)\/auth_subtitles\/(\w+)\.vtt\?(.*)subtype=(Official|External)
      name: DualSubs.Subtitles.Composite.response
      type: response
      require-body: true
    - match: ^https?:\/\/api\.viki\.io\/(.+)\/auth_subtitles\/(\w+)\.vtt\?(.*)subtype=Translate
      name: DualSubs.Subtitles.Translate.response
      type: response
      require-body: true

    - match: ^https?:\/\/epixhls\.akamaized\.net\/(vam|movies)\/(.+)\/([0-9a-f]{8}(-[0-9a-f]{4}){3}-[0-9a-f]{12})\/(master|prog_index|playlist_\d+)\.m3u8
      name: DualSubs.Master.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/epixhls\.akamaized\.net\/(vam|movies)\/(.+)\/subtitles\/(.+)\/media\.m3u8\?(.*)subtype=
      name: DualSubs.Subtitles.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/epixhls\.akamaized\.net\/(vam|movies)\/(.+)\/subtitles\.m3u8\?(.*)subtype=
      name: DualSubs.Subtitles.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/epixhls\.akamaized\.net\/(vam|movies)\/(.+)\/captions_\d+\/(.+)\/fileSequence\d+\.webvtt\?(.*)subtype=(Official|External)
      name: DualSubs.Subtitles.Composite.response
      type: response
      require-body: true
    - match: ^https?:\/\/epixhls\.akamaized\.net\/(vam|movies)\/(.+)\/subtitles\/(.+)\/([0-9a-f]{8}(-[0-9a-f]{4}){3}-[0-9a-f]{12})\?(.*)subtype=(Official|External)
      name: DualSubs.Subtitles.Composite.response
      type: response
      require-body: true
    - match: ^https?:\/\/epixhls\.akamaized\.net\/(vam|movies)\/(.+)\/captions_\d+\/(.+)\/fileSequence\d+\.webvtt\?(.*)subtype=Translate
      name: DualSubs.Subtitles.Translate.response
      type: response
      require-body: true
    - match: ^https?:\/\/epixhls\.akamaized\.net\/(vam|movies)\/(.+)\/subtitles\/(.+)\/([0-9a-f]{8}(-[0-9a-f]{4}){3}-[0-9a-f]{12})\?(.*)subtype=Translate
      name: DualSubs.Subtitles.Translate.response
      type: response
      require-body: true

    - match: ^https?:\/\/(.+)\.live\.epix\.services\/out\/(.+)\/index\.m3u8
      name: DualSubs.Master.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/(.+)\.live\.epix\.services\/out\/(.+)\/index_5_\d+\.m3u8\?(.*)subtype=
      name: DualSubs.Subtitles.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/(.+)\.live\.epix\.services\/out\/(.+)\/index_5_\d+_\d+\.vtt\?(.*)subtype=(Official|External)
      name: DualSubs.Subtitles.Composite.response
      type: response
      require-body: true
    - match: ^https?:\/\/(.+)\.live\.epix\.services\/out\/(.+)\/index_5_\d+_\d+\.vtt\?(.*)subtype=Translate
      name: DualSubs.Subtitles.Translate.response
      type: response
      require-body: true

    - match: ^https?:\/\/media-production\.nebula\.app\/(.+)\/(all|avc_hevc|avc)\.(\w+)\.m3u8
      name: DualSubs.Master.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/media-production\.nebula\.app\/(.+)\/subtitles\/(.+)\/media\.(\w+)\.m3u8\?(.*)subtype=
      name: DualSubs.Subtitles.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/media-production\.nebula\.app\/(.+)\/subtitles\/(.+)\/main\.(\w+)\.vtt\?(.*)subtype=(Official|External)
      name: DualSubs.Subtitles.Composite.response
      type: response
      require-body: true
    - match: ^https?:\/\/media-production\.nebula\.app\/(.+)\/subtitles\/(.+)\/main\.(\w+)\.vtt\?(.*)subtype=Translate
      name: DualSubs.Subtitles.Translate.response
      type: response
      require-body: true

    - match: ^https?:\/\/(.+)\.prd\.pluto\.tv\/v2\/stitch\/hls\/(channel|episode)\/(\w+)\/master\.m3u8
      name: DualSubs.Master.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/(.+)\.prd\.pluto\.tv\/v2\/stitch\/hls\/(channel|episode)\/(\w+)\/subtitle\/(\w+)\/playlist\.m3u8\?(.*)subtype=
      name: DualSubs.Subtitles.m3u8.response
      type: response
      require-body: true
    - match: ^https?:\/\/(.+)\.plutotv\.net\/(.+)\/hls\/(.+)\/(\w+\.m3u8_)?(\d+)\.vtt\?(.*)subtype=(Official|External)
      name: DualSubs.Subtitles.Composite.response
      type: response
      require-body: true
    - match: ^https?:\/\/(.+)\.plutotv\.net\/(.+)\/hls\/(.+)\/(\w+\.m3u8_)?(\d+)\.vtt\?(.*)subtype=Translate
      name: DualSubs.Subtitles.Translate.response
      type: response
      require-body: true

script-providers:
  DualSubs.Master.m3u8.response:
    url: https://raw.githubusercontent.com/DualSubs/Universal/main/js/DualSubs.Master.m3u8.response.js
    interval: 86400
  DualSubs.Subtitles.m3u8.response:
    url: https://raw.githubusercontent.com/DualSubs/Universal/main/js/DualSubs.Subtitles.m3u8.response.js
    interval: 86400
  DualSubs.Subtitles.Composite.response:
    url: https://raw.githubusercontent.com/DualSubs/Universal/main/js/DualSubs.Subtitles.Composite.response.js
    interval: 86400
  DualSubs.Subtitles.Translate.response:
    url: https://raw.githubusercontent.com/DualSubs/Universal/main/js/DualSubs.Subtitles.Translate.response.js
    interval: 86400
