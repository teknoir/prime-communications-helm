# Prime Communications Helm Chart

This chart deploys a Prime Communications site.

> The implementation of the Helm chart is right now the bare minimum to get it to work.
> The purpose of this chart is to prepare proper defaults for the Prime Communications sites.

## Usage in Teknoir platform
Use the HelmChart to deploy the Prime Communications site to a Device.

```yaml
---
apiVersion: helm.cattle.io/v1
kind: HelmChart
metadata:
  name: site-0001
  namespace: default
spec:
  repo: https://teknoir.github.io/prime-communications-helm
  chart: prime-communications
  targetNamespace: default
  valuesContent: |-
    # triton: See the triton-helm chart for details
    # nvr: See the nvr-helm chart for details
    # pipelines: See the pipelines-helm chart for details
    # historian: See the historian-helm chart for details
    # observatory-pipeline: See the observatory-pipeline-helm chart for details
```

## Example values.yaml

```yaml
nvr:
  instances:
    - name: teknoir-nvr-2x3090-se-axis
      camera:
        uri: rtsp://teknoir:Teknoir2023@192.168.2.137/axis-media/media.amp?videocodec=h264&fps=15&resolution=1920x1080
    - name: teknoir-nvr-2x3090-se-anders-test
      camera:
        uri: rtsp://rtsp-video-file-streams:8554/vid5
    - name: teknoir-nvr-2x3090-se-vid1
      camera:
        uri: rtsp://rtsp-video-file-streams:8554/vid1
    - name: teknoir-nvr-2x3090-se-vid2
      camera:
        uri: rtsp://rtsp-video-file-streams:8554/vid2
    - name: teknoir-nvr-2x3090-se-vid3
      camera:
        uri: rtsp://rtsp-video-file-streams:8554/vid3
    - name: teknoir-nvr-2x3090-se-vid4
      camera:
        uri: rtsp://rtsp-video-file-streams:8554/vid4
    - name: teknoir-nvr-2x3090-se-vid5
      camera:
        uri: rtsp://rtsp-video-file-streams:8554/vid5
    - name: teknoir-nvr-2x3090-se-vid6
      camera:
        uri: rtsp://rtsp-video-file-streams:8554/vid6
```

## Adding the repository

```bash
helm repo add teknoir-prime-communications https://teknoir.github.io/prime-communications-helm/
```

## Installing the chart

```bash
helm install prime-communications teknoir-prime-communications/prime-communications -f values.yaml
```