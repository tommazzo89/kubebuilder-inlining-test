# kubebuilder inlining test

This is a test repo to diagnose a possible controller-runtime bug with deserializing inlined structs in a CRD.
See the [this issue](https://github.com/kubernetes-sigs/controller-runtime/issues/2400).

When loading a [Guestbook](./api/v1/guestbook_types.go) using `Client.Get()` in the [Reconcile()](internal/controller/guestbook_controller.go) method, the `GuestbookSpec.GuestbookDefinition` field's values will remain empty, while the values of `GuestbookSpec.GuestbookDefinitionNotInlined` will be filled.

The example resource used in this example is [./config/samples/webapp_v1_guestbook.yaml](./config/samples/webapp_v1_guestbook.yaml).
