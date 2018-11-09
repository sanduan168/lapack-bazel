# Bazel (http://bazel.io/) BUILD file for lapack

config_setting(
    name = "k8",
    values = {"cpu": "k8"},
)

config_setting(
    name = "aarch64",
    values = {"cpu": "aarch64"},
)

filegroup(
    name = "empty",
    srcs = [],
)

cc_library(
    name = "lapack",
    srcs = select({
        ":k8": glob([
             "k8-lib/*.a",
             "k8-lib/*.so*",
         ]),
        ":aarch64": glob(["aarch64-lib/*.so*"]),
        "//conditions:default": [":empty"]
    }),
    linkstatic = True,
    visibility = ["//visibility:public"],
)
